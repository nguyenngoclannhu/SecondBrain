# How to Build Your First Recommendation System (Easy)

![rw-book-cover](https://substackcdn.com/icons/substack/apple-touch-icon-1024x1024.png)

## Metadata
- Author: [[Logan Thorneloe from ML for SWEs]]
- Full Title: How to Build Your First Recommendation System (Easy)
- Category: #articles
- Summary: This guide shows how to build a simple music recommendation system using PyTorch. It covers data loading, a matrix factorization model, training with early stopping, and saving mappings and weights. Finally, it shows serving recommendations with Streamlit and an option to retrain on new data.
- URL: mailto:reader-forwarded-email/8bfe97c14e172ba637a0e02206f02117

## Full Document
##### A step-by-step guide to training and serving a collaborative filtering model to serve users content

While generative AI has caused discussions about the impact of AI to skyrocket, I’d argue recommendation systems are the AI most people should be concerned about. They’ve been around for over a decade and choose what content people consume, what ideas they see, and even influence *how people think*.

Software engineers should understand recommendation systems because **any company serving content to users is using a system similar to this**. Collaborative filtering is simple, intuitive, and very effective.

[![](https://substackcdn.com/image/fetch/$s_!UUKR!,w_500,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff39aac63-172e-4900-9f8d-4d6fa8e7efb5_500x559.jpeg)](https://substack.com/redirect/9769d506-ff62-473e-b76b-a07bfb3f3218?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)This article is a follow-on to a previous case study detailing how collaborative filtering is used by Spotify and how a system like this has impacted the music industry. If you haven’t read that article, **do that first**. It puts everything below into context.

[This is part one of a series. In this part, I detail how Spotify's recommendation system works and the real-world impact it has (both advertently and inadvertently). In the next part, I will go over how to build a simple recommendation system similar to Spotify's.](https://substack.com/redirect/8b068642-557b-40c7-8f18-d32e7fc3d3ad?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)When you’re finished with this article, you will have **trained your own collaborative filtering model** using matrix factorization and be able to **visualize it** in a UI that shows how interacting with content and retraining a model changes recommendations over time.

#### Housekeeping & Things You Should Know

* The complete code for building this collaborative filtering system can be found in the **[ML for SWEs GitHub repo](https://substack.com/redirect/d5588e8e-4e74-4de9-8bab-c99094752a9e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)**. **Please star it** to support ML for SWEs and stay updated when new tutorials are added. This is the first of many ML system tutorials I’ll be putting out.
* Don’t forget about our **[Machine Learning Roadmap](https://substack.com/redirect/eed4587d-99b0-4716-aafb-dda7ec4851bb?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)**. It’s a guide to ML fundamentals that can be completed entirely for free. I spent some time in 2024 curating it and confidently say **it’s the best free ML roadmap available**.
* **I’m going to start including this Housekeeping and What You Should Know sections in each article and make each article about something.** I felt the roundups were too shallow and I wasn’t having fun or learning enough spending my time on them. Instead, each article will have a little roundup section included.
* **ML for SWEs is looking for sponsors!** If you have a job opportunity, developer tool, or want to share anything else that would be beneficial for software engineers working in AI, reach out to me to get it in front of over 10,000 developers. I reserve the right to deny anything I don’t think is helpful. There’s a high bar for what I share with my audience to ensure it’s a good fit for both readers and sponsors.
* I’ll be posting more frequent jobs updates/who’s hiring/the skills you should acquire for paid subscribers in the ML for SWEs Substack chat. Upgrade to paid if you want those.

Part of Machine Learning for Software Engineers is keeping you abreast of the happenings in AI that are actually important. Here are the most important items since our last article:

* OpenAI and Amazon announced a multi-year, [$38B partnership](https://substack.com/redirect/c6880ce4-3803-471f-9514-84cbf72ac20e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) for AWS to provide large-scale compute infrastructure, including NVIDIA GB200s and GB300s.
* Apple is reportedly nearing a deal to pay Google ~$1B annually to use a [custom 1.2T parameter Gemini model](https://substack.com/redirect/78d1d2a2-37e6-4bf6-a76a-e4d149d16c78?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) to power a major Siri update.
* OpenAI announced it now has [over 1 million paying business customers](https://substack.com/redirect/1c4d483f-244e-429f-ab3f-8bebdf5106f7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) and 7 million ChatGPT for Work seats.
* Moonshot AI’s [Kimi K2 Thinking](https://substack.com/redirect/40678cd0-44c5-4bec-b1c7-33f7a13ab430?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) is a new 1T parameter Mixture-of-Experts model (32B active) that uses native INT4 inference for a ~2x speedup.
* NVIDIA reports achieving [4x faster inference for math problem solving](https://substack.com/redirect/9218afc6-db64-440a-8bab-c381bdf5de6e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) using FP8 quantization and kernel optimizations.
* Researchers propose [Continuous Autoregressive Language Models (CALM)](https://substack.com/redirect/df3e2907-10bb-4d14-8c31-494bcdfa92d1?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), which compress tokens into continuous vectors to cut training FLOPs by 44%.
* Terminal-Bench 2.0 was released alongside [Harbor, a new framework](https://substack.com/redirect/d7dc405a-284f-4b40-a5a9-24c5375ae545?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) for testing AI agents in containerized developer environments.
* OpenAI published a post on [understanding prompt injections](https://substack.com/redirect/bb9879d2-c302-4b4f-b41c-021a756dc766?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), which it calls a frontier security challenge requiring multi-layered defenses.
* Wikipedia is urging AI companies to stop scraping and [use its paid Enterprise API](https://substack.com/redirect/fcdfb39f-6394-4c7c-a117-cc68bc164316?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) to support the nonprofit’s servers and mission.
* A new report details [cybersecurity in the era of AI and quantum](https://substack.com/redirect/2d4f82c2-c1ca-4ba6-9e5e-4829e2e1d028?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), highlighting threats from AI-automated attacks and quantum decryption.
* A Stanford study found that 22-25 year-olds in AI-exposed roles, like software development, experienced a [13% employment decline](https://substack.com/redirect/143ea284-1f9f-4ce8-83c9-48e4e8087f03?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) since ChatGPT’s launch. [Credit: [Charlie Guo](https://open.substack.com/users/3625174-charlie-guo?utm_source=mentions)]
* Platforms like Anthropic’s Claude Code are pushing a shift toward [agentic coding](https://substack.com/redirect/35825e1a-968f-4148-8190-6369e3e7d04f?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), where developers orchestrate agent fleets rather than coding line-by-line. [Credit: [MLOps Community](https://open.substack.com/users/179676708-mlops-community?utm_source=mentions)]
* An article explains how models like Qwen3-Next and Kimi Linear are using [hybrid attention mechanisms](https://substack.com/redirect/5801ae24-f773-46c9-8018-b52fda32d61d?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) to achieve O(n) scaling for long contexts. [Credit: [Sebastian Raschka, PhD](https://open.substack.com/users/27393275-sebastian-raschka-phd?utm_source=mentions)]
* OpenAI is offering [a free year of ChatGPT Plus](https://substack.com/redirect/6e9b8881-c4b3-4f00-bece-49f9684cccb7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) to transitioning U.S. servicemembers and veterans.

If you’re particularly interested in one of these things and would like a deep dive, leave a comment and I’ll see what I can do.

**Now onto our collaborative filtering system!**

#### Step 1: Retrieve the Data

For this specific project, we’ll use the **HetRec 2011 Last.fm 2k dataset** to initially train our model and enable retraining based on simulated interactions between users and artists. HetRec 2011 Last.fm 2k is a great example of implicit feedback which is perfect for a recommendation system. It contains a mapping of listening counts between user and artist IDs, each with a given weight to infer preference (i.e. a higher listen count means a user likes an artist).

First, create a file named `last_fm_loader.py`. This will be used to load our dataset and prepare it for training. Include our imports at the top of the file. We’ll get into how we use each in a later section.

```
`import requests
import zipfile
import io
import pandas as pd
import os`
```
Define a class `LastFmLoader` to encapsulate all the data-loading logic. In that class, create two variables: One with the url for downloading our dataset and one naming the directory of the folder we’ll store the dataset in. The `__init__` function initializes placeholders for our dataframes and defines the file paths we expect to find inside the extracted zip.

```
`class LastFmLoader:

 _ZIP_URL = “[https://files.grouplens.org/datasets/hetrec2011/hetrec2011-lastfm-2k.zip](https://files.grouplens.org/datasets/hetrec2011/hetrec2011-lastfm-2k.zip)”
 _DATA_DIR = “lastfm-2k”

 def __init__(self):
 self.interactions = None
 self.artists = None
 self._interactions_file = os.path.join(self._DATA_DIR, ‘user_artists.dat’)
 self._artists_file = os.path.join(self._DATA_DIR, ‘artists.dat’)`
```
Add a private method `_download_data` to this class. This method downloads the zip file from the URL, and extracts its contents into the `_DATA_DIR` skipping this process if the folder for the data already exists. The print statements are niceties for debugging.

```
 `def _download_data(self):
 
 if os.path.exists(self._DATA_DIR):
 print(f”Directory {self._DATA_DIR} already exists. Skipping download.”)
 return
 
 os.makedirs(self._DATA_DIR, exist_ok=True)
 
 print(f”Downloading data from {self._ZIP_URL}...”)
 try:
 response = requests.get(self._ZIP_URL)
 response.raise_for_status() 

 print(’Extracting data...’)
 with zipfile.ZipFile(io.BytesIO(response.content)) as z:
 z.extractall(self._DATA_DIR)

 print(’Download and extraction complete.’)

 except requests.exceptions.RequestException as e:
 print(f”Error downloading file: {e}”)
 raise
 except zipfile.BadZipFile as e:
 print(f”Error extracting file: {e}”)
 raise
 except Exception as e:
 print(f”An error occurred during download/extraction: {e}”)`
```
Add a public `load_data` method. This is the function we’ll call from our training script. It runs `_download_data` to ensure the data is present. Then, it uses `pandas.read_csv` to load the two files we care about to train our model: `user_artists.dat` (which contains `userID`, `artistID`, `weight`) and `artists.dat` (which contains `id`, `name`).

```
 `def load_data(self):

 self._download_data() 

 try:
 print(’Loading interactions data...’)
 self.interactions = pd.read_csv(
 self._interactions_file, 
 sep=’ ‘, 
 header=0, 
 encoding=’utf-8’
 )

 print(’Loading artists data...’)
 self.artists = pd.read_csv(
 self._artists_file,
 sep=’ ‘,
 header=0, 
 encoding=’utf-8’,
 usecols=[’id’, ‘name’] 
 )
 print(’Data loading complete.’)
 
 except FileNotFoundError as e:
 print(f”Error loading data: {e}”)
 raise
 except Exception as e:
 print(f”An error occurred during data loading: {e}”)`
```
Lastly, add a test block at the end of `last_fm_loader.py`. This block runs a simple test showing the columns present in our data if you execute `python last_fm_loader.py` directly. We won’t run our training or serving system from this file, but this is great for testing its functionality.

```
`if __name__ == “__main__”:
 loader = LastFmLoader()
 loader.load_data()
 if loader.interactions is not None:
 print(loader.interactions.head())
 
 if loader.artists is not None:
 print(loader.artists.head())`
```
#### Step 2: Define the Model

Create `model.py`. This will define our `MatrixFactorization` class. Start with the imports from `torch`.

```
`import torch
import torch.nn as nn`
```
Define the `MatrixFactorization` class, inheriting from `torch.nn.Module`. The `__init__` method sets up our learnable parameters. These are the two embedding matrices our model will learn. `nn.Embedding` is a PyTorch layer that acts as a lookup table. `self.user_embedding` will store learned user representations and `self.artist_embedding` will do the same for artists.

`embedding_dim` is the size we choose for those representations. In `__init__`, we also define values for our embedding matrices.

```
`class MatrixFactorization(nn.Module):

 def __init__(self, num_users, num_artists, embedding_dim=500):
 super(MatrixFactorization, self).__init__()

 self.user_embedding = nn.Embedding(num_users, embedding_dim)
 self.artist_embedding = nn.Embedding(num_artists, embedding_dim)

 self.user_embedding.weight.data.uniform_(0, 0.05)
 self.artist_embedding.weight.data.uniform_(0, 0.05)`
```
Now, we define the `forward` method for the class. This is what PyTorch runs when the model is called. It takes a batch of `user` indices and `artist` indices, looks up their corresponding embedding vectors, and then computes the dot product between them as described in our overview of collaborative filtering systems. The `.sum(dim=1)` is how we perform a batched dot product by computing the dot product over a specified dimension. This resulting “score” is our model’s prediction of how much the user likes the artist.

```
 `def forward(self, user, artist):

 user_vector = self.user_embedding(user)
 artist_vector = self.artist_embedding(artist)

 score = (user_vector * artist_vector).sum(dim=1)

 return score`
```
Again, we add a test block at the end of `model.py`. This is a great way to perform a quick test via `python model.py` to make sure our model’s input and output shapes are correct.

```
`if __name__ == “__main__”:

 print(”Testing model.py”)

 test_num_users = 100
 test_num_artists = 50
 test_emb_size = 10

 model = MatrixFactorization(test_num_users, test_num_artists, test_emb_size)
 print(”Model created.”)

 test_user_ids = torch.LongTensor([1, 5, 20, 99])
 test_artist_ids = torch.LongTensor([4, 10, 30, 45])

 predictions = model(test_user_ids, test_artist_ids)
 
 print(f”\nInput user tensor shape: {test_user_ids.shape}”)
 print(f”Input artist tensor shape: {test_artist_ids.shape}”)
 print(f”Output predictions shape: {predictions.shape}”)

 assert predictions.shape == (4,)

 print(”\nModel test passed!”)
 print(”Example predictions (randomly initialized):”)
 print(predictions)`
```
#### Step 3: Train the Model

Create your third file, `train.py`. This script will use the `LastFmLoader` and `MatrixFactorization` classes to train and save our model.

Start with all the necessary imports. Notice that we’re importing our custom classes here.

```
`import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import Dataset, DataLoader
import pandas as pd
from sklearn.model_selection import train_test_split
import numpy as np
import os

from last_fm_loader import LastFmLoader
from model import MatrixFactorization`
```
We define a custom `LastFmDataset` class. `DataLoader` will use this class to retrieve our training data. The `__init__` takes our data (as numpy arrays) and stores them as Tensors. The `__len__` method returns the total number of samples. The `__getitem__` method returns a single sample (one user, artist, and weight) at a given index. These will be used further down.

```
`class LastFmDataset(Dataset):

 def __init__(self, users, artists, weights):
 self.users = torch.LongTensor(users)
 self.artists = torch.LongTensor(artists)
 self.weights = torch.FloatTensor(weights)

 def __len__(self):
 return len(self.weights)

 def __getitem__(self, idx):
 return self.users[idx], self.artists[idx], self.weights[idx]`
```
When training a model, it’s possible to **overfit**. This is when the model “memorizes” the training data but gets *worse* at handling new, unseen data. You know you’re overfitting when your training loss goes down but your validation loss stays higher.

**Early Stopping** is a technique to prevent this. We monitor the validation loss at each epoch. If the loss *stops* improving for a set number of epochs (our `patience`), we stop the training, since continuing would only make the model worse.

We’ll build this logic into a class. The `__init__` method sets up our tracking parameters:

* `patience`: How many epochs to wait for improvement before stopping.
* `delta`: A small amount the loss must improve by to be considered an “improvement”.
* The other variables (`counter`, `best_score`, etc.) are for internal tracking.

```
`class EarlyStopping:

 def __init__(self, patience=5, verbose=False, delta=0, path=’checkpoint.pt’):
 self.patience = patience
 self.verbose = verbose
 self.counter = 0
 self.best_score = None
 self.early_stop = False
 self.val_loss_min = np.inf
 self.delta = delta
 self.path = path`
```
The `__call__` method makes the class instance callable (like a function). We’ll call it at the end of each epoch, passing in the current `val_loss`.

* It checks if this is the best score it has seen.
* If not, it increments a `counter`.
* If the `counter` exceeds our `patience`, it sets the `early_stop` flag to `True`.
* If the score *is* better, it resets the counter and calls `save_checkpoint`.

```
 `def __call__(self, val_loss, model):

 score = -val_loss
 if self.best_score is None:
 self.best_score = score
 self.save_checkpoint(val_loss, model)
 elif score < self.best_score + self.delta:
 self.counter += 1
 if self.verbose:
 print(f’EarlyStopping counter: {self.counter} out of {self.patience}’)
 if self.counter >= self.patience:
 self.early_stop = True
 else:
 self.best_score = score
 self.save_checkpoint(val_loss, model)
 self.counter = 0`
```
The `save_checkpoint` method is a helper called by `__call__`. It’s only triggered when a new best validation loss is found. It saves the model’s current weights to the specified `path`. This ensures that when training stops, the file at `path` contains the weights from the best performing epoch.

```
 `def save_checkpoint(self, val_loss, model):

 if self.verbose:
 print(f’Validation loss decreased ({self.val_loss_min:.6f} --> {val_loss:.6f}). Saving model ...’)
 torch.save(model.state_dict(), self.path)
 self.val_loss_min = val_loss`
```
PyTorch `nn.Embedding` layers need sequential integer indices. The IDs in our data aren’t sequential. Thus, we write a helper function to create two dictionaries: one to map from the original ID to sequential indices, and an inverse mapping to go back.

```
`def create_id_mapping(df):

 user_id_mapping = {original_id: i for i, original_id in enumerate(df[’userID’].unique())}
 artist_id_mapping = {original_id: i for i, original_id in enumerate(df[’artistID’].unique())}

 user_inv_map = {i: original_id for original_id, i in user_id_mapping.items()}
 artist_inv_map = {i: original_id for original_id, i in artist_id_mapping.items()}

 return user_id_mapping, artist_id_mapping, user_inv_map, artist_inv_map`
```
Now we define the main `train_model` function. This first part sets up hyperparameters, creates the `model_store` directory, and loads our data using the `LastFmLoader`. If we were writing a production system, we would run experiments to optimize the hyperparameters. This can be a lengthy process so we’re sticking with guesses and pushing forward.

```
`def train_model(epochs=20, batch_size=1024, emb_size=50, learning_rate=0.001, model_save_path=”model_store/model.pt”):

 os.makedirs(os.path.dirname(model_save_path), exist_ok=True)

 loader = LastFmLoader()
 loader.load_data()
 df = loader.interactions

 if df is None:
 print(”Failed to load data.”)
 return`
```
Still inside `train_model`, we preprocess our data. First, we call `create_id_mapping` to get our dictionaries. Then, we use the `.map()` method to replace the original `userID` and `artistID` columns with their new sequential indices.

```
 `print(”Create ID mappings...”)
 user_id_mapping, artist_id_mapping, user_inv_map, artist_inv_map = create_id_mapping(df)

 df[’userID’] = df[’userID’].map(user_id_mapping)
 df[’artistID’] = df[’artistID’].map(artist_id_mapping)`
```
Next, we apply `np.log1p` to the `weight` column. This `log(1 + x)` transform is useful because it scales down massive listen counts, so a user who listened 100,000 times doesn’t dominate the loss function. We also get the total count of unique users and artists for our model.

```
 `df[’weight_log’] = np.log1p(df[’weight’])

 num_users = len(user_id_mapping)
 num_artists = len(artist_id_mapping)

 print(f”Number of users: {num_users}”)
 print(f”Number of artists: {num_artists}”)`
```
We split our data into an 80% training set and a 20% validation set using `train_test_split`.

```
 `train_df, valid_df = train_test_split(df, test_size=0.2, random_state=42)`
```
We create `LastFmDataset` instances for both the training and validation dataframes.

```
 `train_dataset = LastFmDataset(train_df[’userID’].values, train_df[’artistID’].values, train_df[’weight_log’].values)
 valid_dataset = LastFmDataset(valid_df[’userID’].values, valid_df[’artistID’].values, valid_df[’weight_log’].values)`
```
Then we wrap our `Dataset` instances in `DataLoader`. The `DataLoader` is a PyTorch utility that handles batching, shuffling, and multi-process data loading for us.

```
 `train_loader = DataLoader(train_dataset, batch_size=batch_size, shuffle=True, num_workers=4)
 valid_loader = DataLoader(valid_dataset, batch_size=batch_size, shuffle=False, num_workers=4)`
```
We initialize our `MatrixFactorization` model with the number of users and artists.

```
 `print(”Initializing model...”)
 model = MatrixFactorization(num_users, num_artists, embedding_dim=emb_size)`
```
We check for a GPU (CUDA for NVIDIA, MPS for Apple) and move the model to that device for faster training if available. The `.to(device)` call moves all of the model’s parameters (the embedding matrices) onto the GPU’s memory. The model and data must be on the same device.

```
 `if torch.cuda.is_available():
 device = torch.device(”cuda”)
 elif torch.backends.mps.is_available():
 device = torch.device(”mps”)
 else:
 device = torch.device(”cpu”)
 
 print(f”Using device: {device}”)
 model.to(device)`
```
Then, we define our loss function. MSE is a standard loss function for regression that works by calculating the average squared difference between the model’s prediction and the actual `weight_log`. It heavily penalizes large errors, which is good for this kind of system.

For the optimizer, we choose `optim.Adam` (Adaptive Moment Estimation). Adam is a highly effective and popular optimizer that works well “out of the box” for most problems. It combines the benefits of other optimizers by adapting the learning rate for each model parameter individually, which often leads to faster convergence than standard optimizers like SGD.

We also initialize our `EarlyStopping` class, telling it to save the best model to `model_save_path`.

```
 `loss_fn = nn.MSELoss() 
 optimizer = optim.Adam(model.parameters(), lr=learning_rate, weight_decay=1e-5)
 early_stopper = EarlyStopping(patience=3, verbose=True, path=model_save_path)`
```
This is the core of the training. We loop for `epochs` times. First, we set the model to `model.train()` mode.

```
 `print(”Training model...”)
 for epoch in range(epochs):
 model.train()
 total_train_loss = 0.0`
```
Inside the epoch loop, we loop over every batch in our `train_loader`. For each batch, we move the data to our `device`. This is the second half of the device equation: the model lives on the GPU, so every batch of data we feed it must *also* be moved to the GPU. This `user.to(device)`, `artist.to(device)`, etc. call does that.

```
 `for user, artist, weight in train_loader:
 user, artist, weight = user.to(device), artist.to(device), weight.to(device)`
```
We then get into a standard 5-step PyTorch training process for a batch:

1. `optimizer.zero_grad()`: Clear old gradients.
2. `prediction = model(...)`: Get the model’s prediction.
3. `loss = loss_fn(...)`: Calculate the loss.
4. `loss.backward()`: Compute new gradients.
5. `optimizer.step()`: Update the model’s weights.

We also compute the model’s total training loss as we go along.

```
 `optimizer.zero_grad()
 prediction = model(user, artist)
 loss = loss_fn(prediction, weight)
 loss.backward()
 optimizer.step()
 total_train_loss += loss.item()`
```
After training on all batches, we switch to `model.eval()` mode and use `with torch.no_grad()` to turn off gradient calculations for validation.

```
 `model.eval()
 total_val_loss = 0.0
 with torch.no_grad():`
```
We loop over the `valid_loader` to get the predictions and calculate the total validation loss.

```
 `for users, artists, weights in valid_loader:
 users, artists, weights = users.to(device), artists.to(device), weights.to(device)
 predictions = model(users, artists)
 val_loss = loss_fn(predictions, weights)
 total_val_loss += val_loss.item()`
```
At the end of each epoch, we calculate and print the average training and validation losses.

```
 `avg_train_loss = total_train_loss / len(train_loader)
 avg_val_loss = total_val_loss / len(valid_loader)

 print(f”Epoch {epoch+1}/{epochs} - Train Loss: {avg_train_loss:.4f} - Val Loss: {avg_val_loss:.4f}”)`
```
Finally, we call our `early_stopper` with the validation loss. It will run its internal logic and if the `early_stop` flag has been set to `True`, we break the training loop.

```
 `early_stopper(avg_val_loss, model)
 if early_stopper.early_stop:
 print(”Early stopping triggered.”)
 break`
```
After the loop, the `model_save_path` will hold the best version of our model, thanks to our `EarlyStopping` class. We also *must* save our ID mappings. Without them, we have no way to connect `userID 1002` to `user_index 5`.

```
 `print(f”\nTraining complete. Best model saved to {model_save_path}”)

 mapping_path = “model_store/mappings.pth”
 torch.save({
 ‘user_id_mapping’: user_id_mapping,
 ‘artist_id_mapping’: artist_id_mapping,
 ‘user_inv_map’: user_inv_map,
 ‘artist_inv_map’: artist_inv_map
 }, mapping_path)

 print(f”Mappings saved to {mapping_path}”)`
```
Finally, add the `if __name__ == “__main__”:` block to `train.py` so we can run it as a script using `python train.py`.

```
`if __name__ == “__main__”:
 train_model()`
```
You should now be able to run the full training loop. It will download the data, train the model, and save `model.pt` and `mappings.pth` in the `model_store` directory.

#### Step 4: Serve the Recommendations

Create the final file, `app.py`. We’ll use Streamlit to build a simple web UI.

Import Streamlit, PyTorch, pandas, numpy, and our custom classes. We also import `LastFmDataset` because we’ll need it for retraining. We also define constants for our saved paths.

```
`import streamlit as st
import torch
import pandas as pd
import os
import numpy as np
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader

from model import MatrixFactorization
from last_fm_loader import LastFmLoader
from train import LastFmDataset

MODEL_PATH = os.path.join(”model_store”, “model.pt”)
MAPPINGS_PATH = os.path.join(”model_store”, “mappings.pth”)
SIMULATIONS = 5000`
```
Create a function `load_assets` to load our model, mappings, and artist data. We use Streamlit’s `@st.cache_resource` decorator. This tells Streamlit to run this function *once* and cache the result, so our app is fast and doesn’t reload the model on every interaction.

Inside `load_assets`, we load the mappings. **Note:** `torch.load(MAPPINGS_PATH, weights_only=False)` is important. PyTorch’s security features default to `weights_only=True`, but our mappings file is a dictionary, not model weights.

```
`@st.cache_resource
def load_assets():

 try:
 mappings = torch.load(MAPPINGS_PATH, weights_only=False)
 user_map = mappings[’user_id_mapping’]
 artist_map = mappings[’artist_id_mapping’]
 
 num_users = len(user_map)
 num_artists = len(artist_map)`
```
Now, we initialize a new `MatrixFactorization` model instance and load the saved weights from our `model.pt` file.

```
 `model = MatrixFactorization(num_users, num_artists, embedding_dim=50)
 model.load_state_dict(torch.load(MODEL_PATH))
 model.eval()`
```
Finally, we load the artist names using our `LastFmLoader` so we can display them later, and we return all the loaded assets.

```
 `loader = LastFmLoader()
 loader.load_data()
 artists_df = loader.artists.set_index(’id’)

 return model, mappings, artists_df
 
 except FileNotFoundError as e:
 print(f”Error loading assets: {e}”)
 st.stop()
 except Exception as e:
 print(f”An error occurred during asset loading: {e}”)
 st.stop()`
```
Now we create the get\_recommendations function. This is the core of our app’s logic. We use `@st.cache_data` to cache the results for a given user.

It maps the `selected_user_id` to its `user_idx`, then gets the `user_vector` from the model’s embedding layer *for the current user* and *all* artist vectors from the artist embedding layer.

```
`@st.cache_data(show_spinner=”Generating recommendations...”)
def get_recommendations(selected_user_id, _model, _mappings, _artists_df, num_recs=10):
 user_idx = _mappings[’user_id_mapping’][selected_user_id]
 if user_idx is None:
 st.error(f”User ID {selected_user_id} not found in the mapping.”)
 return pd.DataFrame(columns=[’Artist’, ‘Predicted Score’])
 
 user_tensor = torch.LongTensor([user_idx])
 user_vector = _model.user_embedding(user_tensor)

 all_artist_vectors = _model.artist_embedding.weight`
```
We perform a single matrix multiplication between the one user vector and the entire matrix of artist vectors. This gets us all our predictions for a given user at once.

```
 `with torch.no_grad():
 scores = torch.matmul(user_vector, all_artist_vectors.T). squeeze()`
```
We sort the scores using `torch.argsort` to get the top N, then loop over them, mapping the `artist_model_idx` back to the original artist ID and then to the artist’s name.

```
 `top_indices = torch.argsort(scores, descending=True)[:num_recs]

 rec_data = []
 for idx in top_indices:
 artist_model_idx = idx.item()
 original_artist_id = _mappings[’artist_inv_map’].get(artist_model_idx)
 if original_artist_id:
 artist_name = _artists_df.loc[original_artist_id, ‘name’]
 rec_data.append((artist_name, scores[idx].item()))
 
 return pd.DataFrame(rec_data, columns=[’Artist’, ‘Score’])`
```
To make the visual we want to really understand collaborative filtering, we’ll add functions to simulate new data and retrain the model live. `simulate_new_listen` creates a new dataframe of random user-artist interactions.

```
`def simulate_new_listen(_mappings, num_simulations=100):
 st.write(f”Simulating {num_simulations} new listens...”)
 all_user_indices = list(_mappings[’user_inv_map’].keys())
 all_artist_indices = list(_mappings[’artist_inv_map’].keys())

 sim_users = np.random.choice(all_user_indices, num_simulations)
 sim_artists = np.random.choice(all_artist_indices, num_simulations)
 
 sim_weights = np.random.randint(50, 500, num_simulations)

 sim_df = pd.DataFrame({
 ‘user_idx’: sim_users,
 ‘artist_idx’: sim_artists,
 ‘weight’: sim_weights
 })

 return sim_df`
```
Now we create the `retrain_model` function. It first checks Streamlit’s `st.session_state` to see if a `‘retrained_model’` already exists. If it does, we use that one. If not, then this is the first retraining so we start from the original `load_assets()` model. This ensures that clicking the button multiple times keeps improving the same “live” model.

```
`def retrain_model(new_data): 
 st.sidebar.write(”Retraining model...”)

 if ‘retrained_model’ in st.session_state:
 model_to_retrain = st.session_state.retrained_model
 st.sidebar.write(”Starting from *previously* retrained model.”)
 else:
 model, _, _ = load_assets()
 model_to_retrain = model
 st.sidebar.write(”Starting from *original* loaded model.”)`
```
Next, we prepare the new data. Just like in `train.py`, we apply the `log1p` transform and load the data into a `LastFmDataset` and a `DataLoader`.

```
 `new_data[’weight_log’] = np.log1p(new_data[’weight’])
 new_dataset = LastFmDataset(new_data[’user_idx’].values, new_data[’artist_idx’].values, new_data[’weight_log’].values)
 new_loader = DataLoader(new_dataset, batch_size=32, shuffle=True)`
```
We also need to define our optimizer and loss function again, pointing them at the `model_to_retrain`‘s parameters.

```
 `optimizer = optim.Adam(model_to_retrain.parameters(), lr=0.001)
 loss_fn = nn.MSELoss()`
```
We run a smaller training loop, just on the new data. We set the model to `train()` mode and loop over our `new_loader`, applying the same 5-step PyTorch training process as before.

```
 `model_to_retrain.train()

 for users, artists, weights, in new_loader:
 optimizer.zero_grad()
 predictions = model_to_retrain(users, artists)
 loss = loss_fn(predictions, weights)
 loss.backward()
 optimizer.step()`
```
Finally, we set the model back to `eval()` mode and save the updated model back into `st.session_state[’retrained_model’]`. This replaces the old “live” model with the new, retrained one with the more up to date weights.

```
 `model_to_retrain.eval()
 st.session_state.retrained_model = model_to_retrain
 st.sidebar.success(”Retraining complete!”)`
```
Now we create a simple app to visualize all the calculations that are happen. We’re using Streamlit to keep things simple and build it entirely in Python.

First, the UI loads our assets. Then it checks `st.session_state` to see if a retrained model exists. If so, we use it; otherwise, we use the original model we loaded.

```
`st.set_page_config(page_title=”Music Recommender”, layout=”wide”)
st.title(”Interactive Music Recommender”)

model, mappings, artists_df = load_assets()

if ‘retrained_model’ in st.session_state:
 model_to_use = st.session_state.retrained_model
else:
 model_to_use = model`
```
We create a `st.selectbox` dropdown for the user to pick a user ID.

```
`original_user_ids = list(mappings[’user_inv_map’].values())
st.subheader(”Select a user to see their recommendations:”)
selected_user_id = st.selectbox(”Select a user”, original_user_ids)`
```
If a user is selected, we call `get_recommendations` and display the results in a `st.table`.

```
`if selected_user_id:
 st.write(f”Top Recommendations for user: **{selected_user_id}**”)
 recs_df = get_recommendations(selected_user_id, model_to_use, mappings, artists_df)
 st.table(recs_df.set_index(’Artist’))`
```
Finally, we add a sidebar with a button that, when clicked, runs the simulation and retraining. It then clears the recommendation cache and calls `st.rerun()` to refresh the app and show the new recommendations.

```
`st.sidebar.title(”Retraining Simulation”)
st.sidebar.write(”Simulate new user activity and retrain.”)

if st.sidebar.button(f”Simulate {SIMULATIONS} listens and retrain”):

 new_data = simulate_new_listen(mappings, num_simulations=SIMULATIONS)
 retrain_model(new_data)

 get_recommendations.clear()
 st.rerun()`
```
And that’s it! You’ve built a complete, end-to-end recommendation system with four files.

To see it in action, run the following command in your terminal:

```
`streamlit run app.py`
```
You’ll now be able to select any user, see their initial recommendations, and use the sidebar to simulate new data and retrain the model live to watch how its predictions change over time.

**Always be (machine) learning,**

**Logan**

[Upgrade to paid](https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL3N1YnNjcmliZT91dG1fc291cmNlPXBvc3QmdXRtX2NhbXBhaWduPWVtYWlsLWNoZWNrb3V0Jm5leHQ9aHR0cHMlM0ElMkYlMkZtbGZvcnN3ZXMuY29tJTJGcCUyRmNvbGxhYm9yYXRpdmUtZmlsdGVyaW5nJnI9NnE2ZWdsJnRva2VuPWV5SjFjMlZ5WDJsa0lqbzBNRFkzTmpVM05Ea3NJbWxoZENJNk1UYzJNamcyT1RreE1Dd2laWGh3SWpveE56WTFORFl4T1RFd0xDSnBjM01pT2lKd2RXSXRNVGMwTkRFM09TSXNJbk4xWWlJNkltTm9aV05yYjNWMEluMC5hdnhoazByME16WVJnWmRKWWNTekpkd2tpaXBudm93VW94dTl1cG5jMF9rIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.3owYekc7J3etlWzqcZu3wFNPD38TLz2IBCxwY2m2o-M?&utm_source=substack&utm_medium=email&utm_content=postcta)

[View in app](https://substack.com/app-link/post?publication_id=1744179&post_id=178561311&utm_source=post-email-title&utm_campaign=email-post-title&isFreemail=true&r=6q6egl&token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV_fQzpiADJJXpQ6PyLryMy_c79K3AFegnev20)

<div>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjUxMTExMTQwMzE0LjMuODA1OWZkYmY2NGViYTg1MEBtZy1kMC5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMC5zdWJzdGFjay5jb20iLCJwIjoxNzg1NjEzMTEsInQiOiJuZXdzbGV0dGVyIiwiYSI6ImV2ZXJ5b25lIiwicyI6MTc0NDE3OSwiYyI6InBvc3QiLCJmIjp0cnVlLCJwb3NpdGlvbiI6InRvcCIsImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoxNzY1NDYxOTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImVvIn0.6c2FHlq9sCCDZK51ldWvmwXdYmUPMb6jvLSPR-\_Y20c" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody>
<tr>
<td></td>
<td width="550"></td>
<td></td>
</tr>
<tr>
<td></td>
<td align="left" width="550"><div style="font-size: 16px;line-height: 26px;max-width: 550px;width: 100%;margin: 0 auto;overflow-wrap: break-word;">
<table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr><td align="right" style="height:20px;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><span style="font-family: SF Pro Text, -apple-system, system-ui, BlinkMacSystemFont, Inter, Segoe UI, Roboto, Helvetica, Arial, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol;font-size: 13px;color: unset;list-style: none;text-decoration: unset;margin: 0;"><div style="list-style: none;color: unset;text-align: right;font-size: 12px;line-height: 16px;text-decoration: unset;margin: 0;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;" translated="">Forwarded this email? <a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL3N1YnNjcmliZT91dG1fc291cmNlPWVtYWlsJnV0bV9jYW1wYWlnbj1lbWFpbC1zdWJzY3JpYmUmcj02cTZlZ2wmbmV4dD1odHRwcyUzQSUyRiUyRm1sZm9yc3dlcy5jb20lMkZwJTJGY29sbGFib3JhdGl2ZS1maWx0ZXJpbmciLCJwIjoxNzg1NjEzMTEsInMiOjE3NDQxNzksImYiOnRydWUsInUiOjQwNjc2NTc0OSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjIwNzg0NDU5MTAsImlzcyI6InB1Yi0wIiwic3ViIjoibGluay1yZWRpcmVjdCJ9.t-JdIgk7hs6xKuV2LpCuh-a6ywEV7tNcpoThNNf3HmQ?" style="list-style: none;color: unset;text-decoration: unset;margin: 0;-webkit-text-decoration-line: underline;text-decoration-line: underline;">Subscribe here</a> for more</span></div></span></td></tr></tbody></table></td></tr></tbody></table>
<div dir="auto" style="--image-offset-margin: -120px;padding: 32px 0 0 0;font-size: 16px;line-height: 26px;"><div aria-label="Post header" role="region" style="font-size: 16px;line-height: 26px;">
<h1 dir="auto" style="direction: auto;text-align: start;unicode-bidi: isolate;color: rgb(54,55,55);font-family: Lora,sans-serif;font-weight: 600;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 0;line-height: 36px;font-size: 32px;"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=post-email-title&amp;utm\_campaign=email-post-title&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20" style="color: rgb(54,55,55);text-decoration: none;">How to Build Your First Recommendation System (Easy)</a></h1>
<h3 dir="auto" style="direction: auto;text-align: start;unicode-bidi: isolate;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: normal;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 4px 0 0;color: #777777;line-height: 24px;font-size: 18px;margin-top: 12px;">A step-by-step guide to training and serving a collaborative filtering model to serve users content</h3>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="margin: 1em 0;height: 20px;align-items: center;" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(54,55,55);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;"><a href="https://substack.com/@loganthorneloe" style="list-style: none;color: rgb(54,55,55);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;text-decoration: none">Logan Thorneloe</a></div></td></tr></tbody></table></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;"><time datetime="2025-11-11T14:04:05.497Z">Nov 11</time></div></td></tr></tbody></table></td></tr>
</tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><a href="https://substack.com/@loganthorneloe"><img height="40" src="https://substackcdn.com/image/fetch/%24s\_!jUgr!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdcabb40d-0160-46a4-ad4f-55b486a11ee0\_1024x1024.jpeg" style="box-sizing: border-box;border-radius: 500000px;max-width: 550px;border: none;vertical-align: middle;width: 40px;height: 40px;min-width: 40px;min-height: 40px;object-fit: cover;margin: 0px;display: inline" width="40"/></a></td></tr></tbody></table></td>
</tr></tbody></table>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="border-top: 1px solid rgb(0,0,0,.1);border-bottom: 1px solid rgb(0,0,0,.1);min-width: 100%;" width="100%"><tbody>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;isFreemail=true&amp;submitLike=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwicmVhY3Rpb24iOiLinaQiLCJpYXQiOjE3NjI4Njk5MTAsImV4cCI6MTc2NTQ2MTkxMCwiaXNzIjoicHViLTE3NDQxNzkiLCJzdWIiOiJyZWFjdGlvbiJ9.9nhwnhUeYT9WZh3iZ4tLu53-WXg5OBzr98xKSTMIRms&amp;utm\_medium=email&amp;utm\_campaign=email-reaction&amp;r=6q6egl" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!PeVs!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!x1tS!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideComments%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=share&amp;utm\_campaign=email-share&amp;action=share&amp;triggerShare=true&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!\_L14!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9vcGVuLnN1YnN0YWNrLmNvbS9wdWIvc29jaWV0eXNiYWNrZW5kL3AvY29sbGFib3JhdGl2ZS1maWx0ZXJpbmc\_dXRtX3NvdXJjZT1zdWJzdGFjayZ1dG1fbWVkaXVtPWVtYWlsJnV0bV9jYW1wYWlnbj1lbWFpbC1yZXN0YWNrLWNvbW1lbnQmYWN0aW9uPXJlc3RhY2stY29tbWVudCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09EVTJNVE14TVN3aWFXRjBJam94TnpZeU9EWTVPVEV3TENKbGVIQWlPakUzTmpVME5qRTVNVEFzSW1semN5STZJbkIxWWkweE56UTBNVGM1SWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuOUZyOUpLVl9mUXpwaUFESkpYcFE2UHlMcnlNeV9jNzlLM0FGZWduZXYyMCIsInAiOjE3ODU2MTMxMSwicyI6MTc0NDE3OSwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjI4Njk5MTAsImV4cCI6MjA3ODQ0NTkxMCwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.CBVTBFy6IkXmkon3nthkoiqeJg8YymkwUom5yYFVw1M?&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!5EGt!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
</tr></tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://open.substack.com/pub/societysbackend/p/collaborative-filtering?utm\_source=email&amp;redirect=app-store&amp;utm\_campaign=email-read-in-app" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><div style="font-size: 16px;line-height: 26px;display: inline-block;vertical-align: middle;max-width: 0;min-height: 18px;"></div>
<span style="vertical-align: middle;margin-right: 4px">READ IN APP</span><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!ET-\_!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideArrowUpRight%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="min-width: 18px;min-height: 18px;border: none;vertical-align: middle;margin-right: 0;margin-left: 0;max-width: 18px" width="18"/></a></td></tr></tbody></table></td></tr></tbody></table></td>
</tr></tbody></table></td></tr>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
</tbody></table>
</div></div>
<div dir="auto" style="--image-offset-margin: -120px;padding: 32px 0 0 0;font-size: 16px;line-height: 26px;"><div dir="auto" style="text-align: initial;font-size: 16px;line-height: 26px;width: 100%;word-break: break-word;margin-bottom: 16px;font-family: Spectral,sans-serif;font-weight: 400;">
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;margin-top: 0;"><span>While generative AI has caused discussions about the impact of AI to skyrocket, I’d argue recommendation systems are the AI most people should be concerned about. They’ve been around for over a decade and choose what content people consume, what ideas they see, and even influence </span><em>how people think</em><span>.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Software engineers should understand recommendation systems because </span><strong>any company serving content to users is using a system similar to this</strong><span>. Collaborative filtering is simple, intuitive, and very effective.</span></p>
<div style="font-size: 16px;line-height: 26px;margin: 32px auto;"><figure style="width: 100%;margin: 0 auto;"><table border="0" cellpadding="0" cellspacing="0" data-component-name="Image2ToDOMStatic" style="mso-padding-alt: 1em 0 1.6em;" width="100%"><tbody><tr>
<td style="text-align: center;"></td>
<td align="left" style="text-align: center;" width="500"><a href="https://substack.com/redirect/9769d506-ff62-473e-b76b-a07bfb3f3218?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="position: relative;flex-direction: column;align-items: center;padding: 0;width: auto;height: auto;border: none;text-decoration: none;display: block;margin: 0;" target="\_blank"><img alt="" data-attrs='{"src":"https://substack-post-media.s3.amazonaws.com/public/images/f39aac63-172e-4900-9f8d-4d6fa8e7efb5\_500x559.jpeg","srcNoWatermark":null,"fullscreen":null,"imageSize":null,"height":559,"width":500,"resizeWidth":null,"bytes":null,"alt":null,"title":null,"type":null,"href":null,"belowTheFold":false,"topImage":true,"internalRedirect":null,"isProcessing":false,"align":null,"offset":false}' height="559" src="https://substackcdn.com/image/fetch/%24s\_!UUKR!,w\_500,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff39aac63-172e-4900-9f8d-4d6fa8e7efb5\_500x559.jpeg" style="border: none !important;vertical-align: middle;display: block;-ms-interpolation-mode: bicubic;height: auto;margin-bottom: 0;width: auto !important;max-width: 100% !important;margin: 0 auto;" width="500"/></a></td>
<td style="text-align: center;"></td>
</tr></tbody></table></figure></div>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>This article is a follow-on to a previous case study detailing how collaborative filtering is used by Spotify and how a system like this has impacted the music industry. If you haven’t read that article, </span><strong>do that first</strong><span>. It puts everything below into context.</span></p>
<div data-component-name="DigestPostEmbedStatic" style="margin-bottom: 20px;padding: 0;position: relative;font-size: 16px;line-height: 26px;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><a href="https://substack.com/redirect/8b068642-557b-40c7-8f18-d32e7fc3d3ad?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="text-decoration: none;"><h2 style="list-style: none;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 700;margin: 0;color: #363737;line-height: 36px;font-size: 30px;text-decoration: unset;">Spotify ML Case Study: AI Has Fundamentally Changed the Music Industry</h2></a></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: #777777;margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;"><a href="https://substack.com/profile/43759292-logan-thorneloe" style="color: inherit;text-decoration: none;">Logan Thorneloe</a></div></td>
<td style="min-width: 4px" width="4"></td>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 16px;line-height: 26px;text-decoration: unset;color: #777777;margin: 0;">·</div></td>
</tr></tbody></table></td>
<td style="min-width: 4px" width="4"></td>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: #777777;margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;">Jul 11</div></td>
</tr></tbody></table></td></tr>
<tr><td><div style="text-decoration: unset;list-style: none;padding-top: 24px;font-size: 16px;line-height: 26px;"><a href="https://substack.com/redirect/8b068642-557b-40c7-8f18-d32e7fc3d3ad?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="text-decoration: none;"><picture><source sizes="100vw" srcset="https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 424w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 848w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 1272w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 1300w" type="image/webp"/><img alt="Spotify ML Case Study: AI Has Fundamentally Changed the Music Industry" height="650" sizes="100vw" src="https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ" srcset="https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 424w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 848w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 1272w, https://lh7-rt.googleusercontent.com/docsz/AD\_4nXf71q0JYUlylKJXm64BdZz09ePhWL88ZEDZEu1rD2-gpt46XeneIi47iRZjQhhbLwQu3Mwkk4pJkcs-pM5hMnJGiA1EMIk7glZ1ZiHwUlXOewdQZSh0RHV8ePMVHvVNX1-7of-NEw?key=q\_Uug9PL4P-qjvlr9iZzfQ 1300w" style="text-decoration: unset;list-style: none;border: none !important;vertical-align: middle;display: block;-ms-interpolation-mode: bicubic;max-width: 100%;height: auto;margin: 0 auto;object-fit: cover;width: 100%;max-height: 325px!important;" width="1300"/></picture></a></div></td></tr>
<tr><td><a href="https://substack.com/redirect/8b068642-557b-40c7-8f18-d32e7fc3d3ad?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="text-decoration: none;"><p style="text-decoration: unset;list-style: none;margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">This is part one of a series. In this part, I detail how Spotify's recommendation system works and the real-world impact it has (both advertently and inadvertently). In the next part, I will go over how to build a simple recommendation system similar to Spotify's.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"></p></a></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="padding-top:0px;padding-bottom:0px;" width="auto"><tbody><tr><td style="vertical-align:middle;">
<a href="https://substack.com/redirect/8b068642-557b-40c7-8f18-d32e7fc3d3ad?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="list-style: none;color: unset;text-align: center;text-decoration: unset;margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;"></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><span style="list-style: none;text-decoration: unset;color: rgb(255,103,25);margin: 0;font-size: 14px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read full story</span></td></tr></tbody></table>
</td></tr></tbody></table></td></tr>
</tbody></table></div>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>When you’re finished with this article, you will have </span><strong>trained your own collaborative filtering model</strong><span> using matrix factorization and be able to </span><strong>visualize it</strong><span> in a UI that shows how interacting with content and retraining a model changes recommendations over time.</span></p>
<h2 style="position: relative;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 1em 0 0.625em 0;color: rgb(54,55,55);line-height: 1.16em;font-size: 1.625em;">Housekeeping &amp; Things You Should Know</h2>
<ul style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>The complete code for building this collaborative filtering system can be found in the </span><strong><a href="https://substack.com/redirect/d5588e8e-4e74-4de9-8bab-c99094752a9e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">ML for SWEs GitHub repo</a></strong><span>. </span><strong>Please star it</strong><span> to support ML for SWEs and stay updated when new tutorials are added. This is the first of many ML system tutorials I’ll be putting out.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Don’t forget about our </span><strong><a href="https://substack.com/redirect/eed4587d-99b0-4716-aafb-dda7ec4851bb?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">Machine Learning Roadmap</a></strong><span>. It’s a guide to ML fundamentals that can be completed entirely for free. I spent some time in 2024 curating it and confidently say </span><strong>it’s the best free ML roadmap available</strong><span>.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><strong>I’m going to start including this Housekeeping and What You Should Know sections in each article and make each article about something.</strong><span> I felt the roundups were too shallow and I wasn’t having fun or learning enough spending my time on them. Instead, each article will have a little roundup section included.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><strong>ML for SWEs is looking for sponsors!</strong><span> If you have a job opportunity, developer tool, or want to share anything else that would be beneficial for software engineers working in AI, reach out to me to get it in front of over 10,000 developers. I reserve the right to deny anything I don’t think is helpful. There’s a high bar for what I share with my audience to ensure it’s a good fit for both readers and sponsors.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;">
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;">I’ll be posting more frequent jobs updates/who’s hiring/the skills you should acquire for paid subscribers in the ML for SWEs Substack chat. Upgrade to paid if you want those.</p>
<div data-component-name="SubscribeWidget" style="margin: 0 0 1em;direction: ltr;font-size: 16px;line-height: 26px;"><div style="text-decoration: unset;list-style: none;font-size: 16px;line-height: 26px;text-align: center;cursor: pointer;border-radius: 4px;"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL3N1YnNjcmliZT91dG1fc291cmNlPXBvc3QmdXRtX2NhbXBhaWduPWVtYWlsLWNoZWNrb3V0Jm5leHQ9aHR0cHMlM0ElMkYlMkZtbGZvcnN3ZXMuY29tJTJGcCUyRmNvbGxhYm9yYXRpdmUtZmlsdGVyaW5nJnI9NnE2ZWdsJnRva2VuPWV5SjFjMlZ5WDJsa0lqbzBNRFkzTmpVM05Ea3NJbWxoZENJNk1UYzJNamcyT1RreE1Dd2laWGh3SWpveE56WTFORFl4T1RFd0xDSnBjM01pT2lKd2RXSXRNVGMwTkRFM09TSXNJbk4xWWlJNkltTm9aV05yYjNWMEluMC5hdnhoazByME16WVJnWmRKWWNTekpkd2tpaXBudm93VW94dTl1cG5jMF9rIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.3owYekc7J3etlWzqcZu3wFNPD38TLz2IBCxwY2m2o-M?&amp;utm\_medium=email&amp;utm\_source=subscribe-widget&amp;utm\_content=178561311" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;cursor: pointer;border: none;border-radius: 8px;font-size: 14px;line-height: 20px;font-weight: 600;text-align: center;opacity: 1;outline: none;white-space: nowrap;text-decoration: none !important;margin: 0 auto;background-color: #eb5757;color: #ffffff !important;padding: 12px 20px;height: auto;"><span style="color: #ffffff;text-decoration: none;">Upgrade to paid</span></a></div></div>
</li>
</ul>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Part of Machine Learning for Software Engineers is keeping you abreast of the happenings in AI that are actually important. Here are the most important items since our last article:</p>
<ul style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>OpenAI and Amazon announced a multi-year, </span><a href="https://substack.com/redirect/c6880ce4-3803-471f-9514-84cbf72ac20e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">$38B partnership</a><span> for AWS to provide large-scale compute infrastructure, including NVIDIA GB200s and GB300s.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Apple is reportedly nearing a deal to pay Google ~$1B annually to use a </span><a href="https://substack.com/redirect/78d1d2a2-37e6-4bf6-a76a-e4d149d16c78?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">custom 1.2T parameter Gemini model</a><span> to power a major Siri update.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>OpenAI announced it now has </span><a href="https://substack.com/redirect/1c4d483f-244e-429f-ab3f-8bebdf5106f7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">over 1 million paying business customers</a><span> and 7 million ChatGPT for Work seats.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Moonshot AI’s </span><a href="https://substack.com/redirect/40678cd0-44c5-4bec-b1c7-33f7a13ab430?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">Kimi K2 Thinking</a><span> is a new 1T parameter Mixture-of-Experts model (32B active) that uses native INT4 inference for a ~2x speedup.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>NVIDIA reports achieving </span><a href="https://substack.com/redirect/9218afc6-db64-440a-8bab-c381bdf5de6e?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">4x faster inference for math problem solving</a><span> using FP8 quantization and kernel optimizations.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Researchers propose </span><a href="https://substack.com/redirect/df3e2907-10bb-4d14-8c31-494bcdfa92d1?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">Continuous Autoregressive Language Models (CALM)</a><span>, which compress tokens into continuous vectors to cut training FLOPs by 44%.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Terminal-Bench 2.0 was released alongside </span><a href="https://substack.com/redirect/d7dc405a-284f-4b40-a5a9-24c5375ae545?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">Harbor, a new framework</a><span> for testing AI agents in containerized developer environments.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>OpenAI published a post on </span><a href="https://substack.com/redirect/bb9879d2-c302-4b4f-b41c-021a756dc766?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">understanding prompt injections</a><span>, which it calls a frontier security challenge requiring multi-layered defenses.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Wikipedia is urging AI companies to stop scraping and </span><a href="https://substack.com/redirect/fcdfb39f-6394-4c7c-a117-cc68bc164316?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">use its paid Enterprise API</a><span> to support the nonprofit’s servers and mission.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>A new report details </span><a href="https://substack.com/redirect/2d4f82c2-c1ca-4ba6-9e5e-4829e2e1d028?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">cybersecurity in the era of AI and quantum</a><span>, highlighting threats from AI-automated attacks and quantum decryption.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>A Stanford study found that 22-25 year-olds in AI-exposed roles, like software development, experienced a </span><a href="https://substack.com/redirect/143ea284-1f9f-4ce8-83c9-48e4e8087f03?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">13% employment decline</a><span> since ChatGPT’s launch. [Credit: </span><span data-component-name="MentionStatic" style="white-space: nowrap;cursor: pointer;color: #eb5757;border-radius: 4px;transition: color .25scubic-bezier(.19,1,.22,1),background-color .25scubic-bezier(.19,1,.22,1),box-shadow .25scubic-bezier(.19,1,.22,1),border .25scubic-bezier(.19,1,.22,1),border-radius .25scubic-bezier(.19,1,.22,1),opacity .25scubic-bezier(.19,1,.22,1),filter .25scubic-bezier(.19,1,.22,1),stroke .25scubic-bezier(.19,1,.22,1),transform .25scubic-bezier(.19,1,.22,1),scale .25scubic-bezier(.19,1,.22,1),outline .25scubic-bezier(.19,1,.22,1);margin: 0 -.125em;padding: 0 .125em .0625em;text-decoration: none;"><a href="https://open.substack.com/users/3625174-charlie-guo?utm\_source=mentions" style="-webkit-text-decoration: none;color: #eb5757;text-decoration: none;">Charlie Guo</a></span><span>]</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>Platforms like Anthropic’s Claude Code are pushing a shift toward </span><a href="https://substack.com/redirect/35825e1a-968f-4148-8190-6369e3e7d04f?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">agentic coding</a><span>, where developers orchestrate agent fleets rather than coding line-by-line. [Credit: </span><span data-component-name="MentionStatic" style="white-space: nowrap;cursor: pointer;color: #eb5757;border-radius: 4px;transition: color .25scubic-bezier(.19,1,.22,1),background-color .25scubic-bezier(.19,1,.22,1),box-shadow .25scubic-bezier(.19,1,.22,1),border .25scubic-bezier(.19,1,.22,1),border-radius .25scubic-bezier(.19,1,.22,1),opacity .25scubic-bezier(.19,1,.22,1),filter .25scubic-bezier(.19,1,.22,1),stroke .25scubic-bezier(.19,1,.22,1),transform .25scubic-bezier(.19,1,.22,1),scale .25scubic-bezier(.19,1,.22,1),outline .25scubic-bezier(.19,1,.22,1);margin: 0 -.125em;padding: 0 .125em .0625em;text-decoration: none;"><a href="https://open.substack.com/users/179676708-mlops-community?utm\_source=mentions" style="-webkit-text-decoration: none;color: #eb5757;text-decoration: none;">MLOps Community</a></span><span>]</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>An article explains how models like Qwen3-Next and Kimi Linear are using </span><a href="https://substack.com/redirect/5801ae24-f773-46c9-8018-b52fda32d61d?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">hybrid attention mechanisms</a><span> to achieve O(n) scaling for long contexts. [Credit: </span><span data-component-name="MentionStatic" style="white-space: nowrap;cursor: pointer;color: #eb5757;border-radius: 4px;transition: color .25scubic-bezier(.19,1,.22,1),background-color .25scubic-bezier(.19,1,.22,1),box-shadow .25scubic-bezier(.19,1,.22,1),border .25scubic-bezier(.19,1,.22,1),border-radius .25scubic-bezier(.19,1,.22,1),opacity .25scubic-bezier(.19,1,.22,1),filter .25scubic-bezier(.19,1,.22,1),stroke .25scubic-bezier(.19,1,.22,1),transform .25scubic-bezier(.19,1,.22,1),scale .25scubic-bezier(.19,1,.22,1),outline .25scubic-bezier(.19,1,.22,1);margin: 0 -.125em;padding: 0 .125em .0625em;text-decoration: none;"><a href="https://open.substack.com/users/27393275-sebastian-raschka-phd?utm\_source=mentions" style="-webkit-text-decoration: none;color: #eb5757;text-decoration: none;">Sebastian Raschka, PhD</a></span><span>]</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>OpenAI is offering </span><a href="https://substack.com/redirect/6e9b8881-c4b3-4f00-bece-49f9684cccb7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: #eb5757;text-decoration: none;">a free year of ChatGPT Plus</a><span> to transitioning U.S. servicemembers and veterans.</span></p></li>
</ul>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">If you’re particularly interested in one of these things and would like a deep dive, leave a comment and I’ll see what I can do.</p>
<p data-attrs='{"url":"https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment","text":"Leave a comment","action":null,"class":null}' data-component-name="ButtonCreateButton" style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;text-align: center;cursor: pointer;border-radius: 4px;"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment" rel="" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;cursor: pointer;border: none;border-radius: 8px;font-size: 14px;line-height: 20px;font-weight: 600;text-align: center;margin: 0;opacity: 1;outline: none;white-space: nowrap;color: #ffffff !important;text-decoration: none !important;background-color: #eb5757;padding: 12px 20px;height: auto;"><span style="color: #ffffff;text-decoration: none;">Leave a comment</span></a></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><strong>Now onto our collaborative filtering system!</strong></p>
<h2 style="position: relative;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 1em 0 0.625em 0;color: rgb(54,55,55);line-height: 1.16em;font-size: 1.625em;">Step 1: Retrieve the Data</h2>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>For this specific project, we’ll use the </span><strong>HetRec 2011 Last.fm 2k dataset</strong><span> to initially train our model and enable retraining based on simulated interactions between users and artists. HetRec 2011 Last.fm 2k is a great example of implicit feedback which is perfect for a recommendation system. It contains a mapping of listening counts between user and artist IDs, each with a given weight to infer preference (i.e. a higher listen count means a user likes an artist).</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>First, create a file named </span><code>last\_fm\_loader.py</code><span>. This will be used to load our dataset and prepare it for training. Include our imports at the top of the file. We’ll get into how we use each in a later section.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">import requests
import zipfile
import io
import pandas as pd
import os</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Define a class </span><code>LastFmLoader</code><span> to encapsulate all the data-loading logic. In that class, create two variables: One with the url for downloading our dataset and one naming the directory of the folder we’ll store the dataset in. The </span><code>\_\_init\_\_</code><span> function initializes placeholders for our dataframes and defines the file paths we expect to find inside the extracted zip.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">class LastFmLoader:

 \_ZIP\_URL = “[https://files.grouplens.org/datasets/hetrec2011/hetrec2011-lastfm-2k.zip](https://files.grouplens.org/datasets/hetrec2011/hetrec2011-lastfm-2k.zip)”
 \_DATA\_DIR = “lastfm-2k”

 def \_\_init\_\_(self):
 self.interactions = None
 self.artists = None
 self.\_interactions\_file = os.path.join(self.\_DATA\_DIR, ‘user\_artists.dat’)
 self.\_artists\_file = os.path.join(self.\_DATA\_DIR, ‘artists.dat’)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Add a private method </span><code>\_download\_data</code><span> to this class. This method downloads the zip file from the URL, and extracts its contents into the </span><code>\_DATA\_DIR</code><span> skipping this process if the folder for the data already exists. The print statements are niceties for debugging.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> def \_download\_data(self):
 
 if os.path.exists(self.\_DATA\_DIR):
 print(f”Directory {self.\_DATA\_DIR} already exists. Skipping download.”)
 return
 
 os.makedirs(self.\_DATA\_DIR, exist\_ok=True)
 
 print(f”Downloading data from {self.\_ZIP\_URL}...”)
 try:
 response = requests.get(self.\_ZIP\_URL)
 response.raise\_for\_status() 

 print(’Extracting data...’)
 with zipfile.ZipFile(io.BytesIO(response.content)) as z:
 z.extractall(self.\_DATA\_DIR)

 print(’Download and extraction complete.’)

 except requests.exceptions.RequestException as e:
 print(f”Error downloading file: {e}”)
 raise
 except zipfile.BadZipFile as e:
 print(f”Error extracting file: {e}”)
 raise
 except Exception as e:
 print(f”An error occurred during download/extraction: {e}”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Add a public </span><code>load\_data</code><span> method. This is the function we’ll call from our training script. It runs </span><code>\_download\_data</code><span> to ensure the data is present. Then, it uses </span><code>pandas.read\_csv</code><span> to load the two files we care about to train our model: </span><code>user\_artists.dat</code><span> (which contains </span><code>userID</code><span>, </span><code>artistID</code><span>, </span><code>weight</code><span>) and </span><code>artists.dat</code><span> (which contains </span><code>id</code><span>, </span><code>name</code><span>).</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> def load\_data(self):

 self.\_download\_data() 

 try:
 print(’Loading interactions data...’)
 self.interactions = pd.read\_csv(
 self.\_interactions\_file, 
 sep=’ ‘, 
 header=0, 
 encoding=’utf-8’
 )

 print(’Loading artists data...’)
 self.artists = pd.read\_csv(
 self.\_artists\_file,
 sep=’ ‘,
 header=0, 
 encoding=’utf-8’,
 usecols=[’id’, ‘name’] 
 )
 print(’Data loading complete.’)
 
 except FileNotFoundError as e:
 print(f”Error loading data: {e}”)
 raise
 except Exception as e:
 print(f”An error occurred during data loading: {e}”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Lastly, add a test block at the end of </span><code>last\_fm\_loader.py</code><span>. This block runs a simple test showing the columns present in our data if you execute </span><code>python last\_fm\_loader.py</code><span> directly. We won’t run our training or serving system from this file, but this is great for testing its functionality.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">if \_\_name\_\_ == “\_\_main\_\_”:
 loader = LastFmLoader()
 loader.load\_data()
 if loader.interactions is not None:
 print(loader.interactions.head())
 
 if loader.artists is not None:
 print(loader.artists.head())</code></code></pre>
<h2 style="position: relative;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 1em 0 0.625em 0;color: rgb(54,55,55);line-height: 1.16em;font-size: 1.625em;">Step 2: Define the Model</h2>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Create </span><code>model.py</code><span>. This will define our </span><code>MatrixFactorization</code><span> class. Start with the imports from </span><code>torch</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">import torch
import torch.nn as nn</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Define the </span><code>MatrixFactorization</code><span> class, inheriting from </span><code>torch.nn.Module</code><span>. The </span><code>\_\_init\_\_</code><span> method sets up our learnable parameters. These are the two embedding matrices our model will learn. </span><code>nn.Embedding</code><span> is a PyTorch layer that acts as a lookup table. </span><code>self.user\_embedding</code><span> will store learned user representations and </span><code>self.artist\_embedding</code><span> will do the same for artists.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><code>embedding\_dim</code><span> is the size we choose for those representations. In </span><code>\_\_init\_\_</code><span>, we also define values for our embedding matrices.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">class MatrixFactorization(nn.Module):

 def \_\_init\_\_(self, num\_users, num\_artists, embedding\_dim=500):
 super(MatrixFactorization, self).\_\_init\_\_()

 self.user\_embedding = nn.Embedding(num\_users, embedding\_dim)
 self.artist\_embedding = nn.Embedding(num\_artists, embedding\_dim)

 self.user\_embedding.weight.data.uniform\_(0, 0.05)
 self.artist\_embedding.weight.data.uniform\_(0, 0.05)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Now, we define the </span><code>forward</code><span> method for the class. This is what PyTorch runs when the model is called. It takes a batch of </span><code>user</code><span> indices and </span><code>artist</code><span> indices, looks up their corresponding embedding vectors, and then computes the dot product between them as described in our overview of collaborative filtering systems. The </span><code>.sum(dim=1)</code><span> is how we perform a batched dot product by computing the dot product over a specified dimension. This resulting “score” is our model’s prediction of how much the user likes the artist.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> def forward(self, user, artist):

 user\_vector = self.user\_embedding(user)
 artist\_vector = self.artist\_embedding(artist)

 score = (user\_vector \* artist\_vector).sum(dim=1)

 return score</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Again, we add a test block at the end of </span><code>model.py</code><span>. This is a great way to perform a quick test via </span><code>python model.py</code><span> to make sure our model’s input and output shapes are correct.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">if \_\_name\_\_ == “\_\_main\_\_”:

 print(”Testing model.py”)

 test\_num\_users = 100
 test\_num\_artists = 50
 test\_emb\_size = 10

 model = MatrixFactorization(test\_num\_users, test\_num\_artists, test\_emb\_size)
 print(”Model created.”)

 test\_user\_ids = torch.LongTensor([1, 5, 20, 99])
 test\_artist\_ids = torch.LongTensor([4, 10, 30, 45])

 predictions = model(test\_user\_ids, test\_artist\_ids)
 
 print(f”\nInput user tensor shape: {test\_user\_ids.shape}”)
 print(f”Input artist tensor shape: {test\_artist\_ids.shape}”)
 print(f”Output predictions shape: {predictions.shape}”)

 assert predictions.shape == (4,)

 print(”\nModel test passed!”)
 print(”Example predictions (randomly initialized):”)
 print(predictions)</code></code></pre>
<h2 style="position: relative;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 1em 0 0.625em 0;color: rgb(54,55,55);line-height: 1.16em;font-size: 1.625em;">Step 3: Train the Model</h2>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Create your third file, </span><code>train.py</code><span>. This script will use the </span><code>LastFmLoader</code><span> and </span><code>MatrixFactorization</code><span> classes to train and save our model.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Start with all the necessary imports. Notice that we’re importing our custom classes here.</p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import Dataset, DataLoader
import pandas as pd
from sklearn.model\_selection import train\_test\_split
import numpy as np
import os

from last\_fm\_loader import LastFmLoader
from model import MatrixFactorization</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We define a custom </span><code>LastFmDataset</code><span> class. </span><code>DataLoader</code><span> will use this class to retrieve our training data. The </span><code>\_\_init\_\_</code><span> takes our data (as numpy arrays) and stores them as Tensors. The </span><code>\_\_len\_\_</code><span> method returns the total number of samples. The </span><code>\_\_getitem\_\_</code><span> method returns a single sample (one user, artist, and weight) at a given index. These will be used further down.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">class LastFmDataset(Dataset):

 def \_\_init\_\_(self, users, artists, weights):
 self.users = torch.LongTensor(users)
 self.artists = torch.LongTensor(artists)
 self.weights = torch.FloatTensor(weights)

 def \_\_len\_\_(self):
 return len(self.weights)

 def \_\_getitem\_\_(self, idx):
 return self.users[idx], self.artists[idx], self.weights[idx]</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>When training a model, it’s possible to </span><strong>overfit</strong><span>. This is when the model “memorizes” the training data but gets </span><em>worse</em><span> at handling new, unseen data. You know you’re overfitting when your training loss goes down but your validation loss stays higher.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><strong>Early Stopping</strong><span> is a technique to prevent this. We monitor the validation loss at each epoch. If the loss </span><em>stops</em><span> improving for a set number of epochs (our </span><code>patience</code><span>), we stop the training, since continuing would only make the model worse.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We’ll build this logic into a class. The </span><code>\_\_init\_\_</code><span> method sets up our tracking parameters:</span></p>
<ul style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>patience</code><span>: How many epochs to wait for improvement before stopping.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>delta</code><span>: A small amount the loss must improve by to be considered an “improvement”.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>The other variables (</span><code>counter</code><span>, </span><code>best\_score</code><span>, etc.) are for internal tracking.</span></p></li>
</ul>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">class EarlyStopping:

 def \_\_init\_\_(self, patience=5, verbose=False, delta=0, path=’checkpoint.pt’):
 self.patience = patience
 self.verbose = verbose
 self.counter = 0
 self.best\_score = None
 self.early\_stop = False
 self.val\_loss\_min = np.inf
 self.delta = delta
 self.path = path</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>The </span><code>\_\_call\_\_</code><span> method makes the class instance callable (like a function). We’ll call it at the end of each epoch, passing in the current </span><code>val\_loss</code><span>.</span></p>
<ul style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;">It checks if this is the best score it has seen.</p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>If not, it increments a </span><code>counter</code><span>.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>If the </span><code>counter</code><span> exceeds our </span><code>patience</code><span>, it sets the </span><code>early\_stop</code><span> flag to </span><code>True</code><span>.</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><span>If the score </span><em>is</em><span> better, it resets the counter and calls </span><code>save\_checkpoint</code><span>.</span></p></li>
</ul>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> def \_\_call\_\_(self, val\_loss, model):

 score = -val\_loss
 if self.best\_score is None:
 self.best\_score = score
 self.save\_checkpoint(val\_loss, model)
 elif score &lt; self.best\_score + self.delta:
 self.counter += 1
 if self.verbose:
 print(f’EarlyStopping counter: {self.counter} out of {self.patience}’)
 if self.counter &gt;= self.patience:
 self.early\_stop = True
 else:
 self.best\_score = score
 self.save\_checkpoint(val\_loss, model)
 self.counter = 0</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>The </span><code>save\_checkpoint</code><span> method is a helper called by </span><code>\_\_call\_\_</code><span>. It’s only triggered when a new best validation loss is found. It saves the model’s current weights to the specified </span><code>path</code><span>. This ensures that when training stops, the file at </span><code>path</code><span> contains the weights from the best performing epoch.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> def save\_checkpoint(self, val\_loss, model):

 if self.verbose:
 print(f’Validation loss decreased ({self.val\_loss\_min:.6f} --&gt; {val\_loss:.6f}). Saving model ...’)
 torch.save(model.state\_dict(), self.path)
 self.val\_loss\_min = val\_loss</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>PyTorch </span><code>nn.Embedding</code><span> layers need sequential integer indices. The IDs in our data aren’t sequential. Thus, we write a helper function to create two dictionaries: one to map from the original ID to sequential indices, and an inverse mapping to go back.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">def create\_id\_mapping(df):

 user\_id\_mapping = {original\_id: i for i, original\_id in enumerate(df[’userID’].unique())}
 artist\_id\_mapping = {original\_id: i for i, original\_id in enumerate(df[’artistID’].unique())}

 user\_inv\_map = {i: original\_id for original\_id, i in user\_id\_mapping.items()}
 artist\_inv\_map = {i: original\_id for original\_id, i in artist\_id\_mapping.items()}

 return user\_id\_mapping, artist\_id\_mapping, user\_inv\_map, artist\_inv\_map</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Now we define the main </span><code>train\_model</code><span> function. This first part sets up hyperparameters, creates the </span><code>model\_store</code><span> directory, and loads our data using the </span><code>LastFmLoader</code><span>. If we were writing a production system, we would run experiments to optimize the hyperparameters. This can be a lengthy process so we’re sticking with guesses and pushing forward.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">def train\_model(epochs=20, batch\_size=1024, emb\_size=50, learning\_rate=0.001, model\_save\_path=”model\_store/model.pt”):

 os.makedirs(os.path.dirname(model\_save\_path), exist\_ok=True)

 loader = LastFmLoader()
 loader.load\_data()
 df = loader.interactions

 if df is None:
 print(”Failed to load data.”)
 return</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Still inside </span><code>train\_model</code><span>, we preprocess our data. First, we call </span><code>create\_id\_mapping</code><span> to get our dictionaries. Then, we use the </span><code>.map()</code><span> method to replace the original </span><code>userID</code><span> and </span><code>artistID</code><span> columns with their new sequential indices.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> print(”Create ID mappings...”)
 user\_id\_mapping, artist\_id\_mapping, user\_inv\_map, artist\_inv\_map = create\_id\_mapping(df)

 df[’userID’] = df[’userID’].map(user\_id\_mapping)
 df[’artistID’] = df[’artistID’].map(artist\_id\_mapping)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Next, we apply </span><code>np.log1p</code><span> to the </span><code>weight</code><span> column. This </span><code>log(1 + x)</code><span> transform is useful because it scales down massive listen counts, so a user who listened 100,000 times doesn’t dominate the loss function. We also get the total count of unique users and artists for our model.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> df[’weight\_log’] = np.log1p(df[’weight’])

 num\_users = len(user\_id\_mapping)
 num\_artists = len(artist\_id\_mapping)

 print(f”Number of users: {num\_users}”)
 print(f”Number of artists: {num\_artists}”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We split our data into an 80% training set and a 20% validation set using </span><code>train\_test\_split</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> train\_df, valid\_df = train\_test\_split(df, test\_size=0.2, random\_state=42)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We create </span><code>LastFmDataset</code><span> instances for both the training and validation dataframes.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> train\_dataset = LastFmDataset(train\_df[’userID’].values, train\_df[’artistID’].values, train\_df[’weight\_log’].values)
 valid\_dataset = LastFmDataset(valid\_df[’userID’].values, valid\_df[’artistID’].values, valid\_df[’weight\_log’].values)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Then we wrap our </span><code>Dataset</code><span> instances in </span><code>DataLoader</code><span>. The </span><code>DataLoader</code><span> is a PyTorch utility that handles batching, shuffling, and multi-process data loading for us.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> train\_loader = DataLoader(train\_dataset, batch\_size=batch\_size, shuffle=True, num\_workers=4)
 valid\_loader = DataLoader(valid\_dataset, batch\_size=batch\_size, shuffle=False, num\_workers=4)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We initialize our </span><code>MatrixFactorization</code><span> model with the number of users and artists.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> print(”Initializing model...”)
 model = MatrixFactorization(num\_users, num\_artists, embedding\_dim=emb\_size)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We check for a GPU (CUDA for NVIDIA, MPS for Apple) and move the model to that device for faster training if available. The </span><code>.to(device)</code><span> call moves all of the model’s parameters (the embedding matrices) onto the GPU’s memory. The model and data must be on the same device.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> if torch.cuda.is\_available():
 device = torch.device(”cuda”)
 elif torch.backends.mps.is\_available():
 device = torch.device(”mps”)
 else:
 device = torch.device(”cpu”)
 
 print(f”Using device: {device}”)
 model.to(device)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Then, we define our loss function. MSE is a standard loss function for regression that works by calculating the average squared difference between the model’s prediction and the actual </span><code>weight\_log</code><span>. It heavily penalizes large errors, which is good for this kind of system.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>For the optimizer, we choose </span><code>optim.Adam</code><span> (Adaptive Moment Estimation). Adam is a highly effective and popular optimizer that works well “out of the box” for most problems. It combines the benefits of other optimizers by adapting the learning rate for each model parameter individually, which often leads to faster convergence than standard optimizers like SGD.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We also initialize our </span><code>EarlyStopping</code><span> class, telling it to save the best model to </span><code>model\_save\_path</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> loss\_fn = nn.MSELoss() 
 optimizer = optim.Adam(model.parameters(), lr=learning\_rate, weight\_decay=1e-5)
 early\_stopper = EarlyStopping(patience=3, verbose=True, path=model\_save\_path)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>This is the core of the training. We loop for </span><code>epochs</code><span> times. First, we set the model to </span><code>model.train()</code><span> mode.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> print(”Training model...”)
 for epoch in range(epochs):
 model.train()
 total\_train\_loss = 0.0</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Inside the epoch loop, we loop over every batch in our </span><code>train\_loader</code><span>. For each batch, we move the data to our </span><code>device</code><span>. This is the second half of the device equation: the model lives on the GPU, so every batch of data we feed it must </span><em>also</em><span> be moved to the GPU. This </span><code>user.to(device)</code><span>, </span><code>artist.to(device)</code><span>, etc. call does that.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> for user, artist, weight in train\_loader:
 user, artist, weight = user.to(device), artist.to(device), weight.to(device)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">We then get into a standard 5-step PyTorch training process for a batch:</p>
<ol style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>optimizer.zero\_grad()</code><span>: Clear old gradients.</span></p></li>
<li style="margin: 8px 0 0 32px;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>prediction = model(...)</code><span>: Get the model’s prediction.</span></p></li>
<li style="margin: 8px 0 0 32px;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>loss = loss\_fn(...)</code><span>: Calculate the loss.</span></p></li>
<li style="margin: 8px 0 0 32px;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>loss.backward()</code><span>: Compute new gradients.</span></p></li>
<li style="margin: 8px 0 0 32px;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><code>optimizer.step()</code><span>: Update the model’s weights.</span></p></li>
</ol>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">We also compute the model’s total training loss as we go along.</p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> optimizer.zero\_grad()
 prediction = model(user, artist)
 loss = loss\_fn(prediction, weight)
 loss.backward()
 optimizer.step()
 total\_train\_loss += loss.item()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>After training on all batches, we switch to </span><code>model.eval()</code><span> mode and use </span><code>with torch.no\_grad()</code><span> to turn off gradient calculations for validation.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> model.eval()
 total\_val\_loss = 0.0
 with torch.no\_grad():</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We loop over the </span><code>valid\_loader</code><span> to get the predictions and calculate the total validation loss.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> for users, artists, weights in valid\_loader:
 users, artists, weights = users.to(device), artists.to(device), weights.to(device)
 predictions = model(users, artists)
 val\_loss = loss\_fn(predictions, weights)
 total\_val\_loss += val\_loss.item()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">At the end of each epoch, we calculate and print the average training and validation losses.</p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> avg\_train\_loss = total\_train\_loss / len(train\_loader)
 avg\_val\_loss = total\_val\_loss / len(valid\_loader)

 print(f”Epoch {epoch+1}/{epochs} - Train Loss: {avg\_train\_loss:.4f} - Val Loss: {avg\_val\_loss:.4f}”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Finally, we call our </span><code>early\_stopper</code><span> with the validation loss. It will run its internal logic and if the </span><code>early\_stop</code><span> flag has been set to </span><code>True</code><span>, we break the training loop.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> early\_stopper(avg\_val\_loss, model)
 if early\_stopper.early\_stop:
 print(”Early stopping triggered.”)
 break</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>After the loop, the </span><code>model\_save\_path</code><span> will hold the best version of our model, thanks to our </span><code>EarlyStopping</code><span> class. We also </span><em>must</em><span> save our ID mappings. Without them, we have no way to connect </span><code>userID 1002</code><span> to </span><code>user\_index 5</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> print(f”\nTraining complete. Best model saved to {model\_save\_path}”)

 mapping\_path = “model\_store/mappings.pth”
 torch.save({
 ‘user\_id\_mapping’: user\_id\_mapping,
 ‘artist\_id\_mapping’: artist\_id\_mapping,
 ‘user\_inv\_map’: user\_inv\_map,
 ‘artist\_inv\_map’: artist\_inv\_map
 }, mapping\_path)

 print(f”Mappings saved to {mapping\_path}”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Finally, add the </span><code>if \_\_name\_\_ == “\_\_main\_\_”:</code><span> block to </span><code>train.py</code><span> so we can run it as a script using </span><code>python train.py</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">if \_\_name\_\_ == “\_\_main\_\_”:
 train\_model()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>You should now be able to run the full training loop. It will download the data, train the model, and save </span><code>model.pt</code><span> and </span><code>mappings.pth</code><span> in the </span><code>model\_store</code><span> directory.</span></p>
<h2 style="position: relative;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 1em 0 0.625em 0;color: rgb(54,55,55);line-height: 1.16em;font-size: 1.625em;">Step 4: Serve the Recommendations</h2>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Create the final file, </span><code>app.py</code><span>. We’ll use Streamlit to build a simple web UI.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Import Streamlit, PyTorch, pandas, numpy, and our custom classes. We also import </span><code>LastFmDataset</code><span> because we’ll need it for retraining. We also define constants for our saved paths.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">import streamlit as st
import torch
import pandas as pd
import os
import numpy as np
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader

from model import MatrixFactorization
from last\_fm\_loader import LastFmLoader
from train import LastFmDataset

MODEL\_PATH = os.path.join(”model\_store”, “model.pt”)
MAPPINGS\_PATH = os.path.join(”model\_store”, “mappings.pth”)
SIMULATIONS = 5000</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Create a function </span><code>load\_assets</code><span> to load our model, mappings, and artist data. We use Streamlit’s </span><code>@st.cache\_resource</code><span> decorator. This tells Streamlit to run this function </span><em>once</em><span> and cache the result, so our app is fast and doesn’t reload the model on every interaction.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Inside </span><code>load\_assets</code><span>, we load the mappings. </span><strong>Note:</strong><span> </span><code>torch.load(MAPPINGS\_PATH, weights\_only=False)</code><span> is important. PyTorch’s security features default to </span><code>weights\_only=True</code><span>, but our mappings file is a dictionary, not model weights.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">@st.cache\_resource
def load\_assets():

 try:
 mappings = torch.load(MAPPINGS\_PATH, weights\_only=False)
 user\_map = mappings[’user\_id\_mapping’]
 artist\_map = mappings[’artist\_id\_mapping’]
 
 num\_users = len(user\_map)
 num\_artists = len(artist\_map)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Now, we initialize a new </span><code>MatrixFactorization</code><span> model instance and load the saved weights from our </span><code>model.pt</code><span> file.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> model = MatrixFactorization(num\_users, num\_artists, embedding\_dim=50)
 model.load\_state\_dict(torch.load(MODEL\_PATH))
 model.eval()
</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Finally, we load the artist names using our </span><code>LastFmLoader</code><span> so we can display them later, and we return all the loaded assets.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> loader = LastFmLoader()
 loader.load\_data()
 artists\_df = loader.artists.set\_index(’id’)

 return model, mappings, artists\_df
 
 except FileNotFoundError as e:
 print(f”Error loading assets: {e}”)
 st.stop()
 except Exception as e:
 print(f”An error occurred during asset loading: {e}”)
 st.stop()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Now we create the get\_recommendations function. This is the core of our app’s logic. We use </span><code>@st.cache\_data</code><span> to cache the results for a given user.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>It maps the </span><code>selected\_user\_id</code><span> to its </span><code>user\_idx</code><span>, then gets the </span><code>user\_vector</code><span> from the model’s embedding layer </span><em>for the current user</em><span> and </span><em>all</em><span> artist vectors from the artist embedding layer.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">@st.cache\_data(show\_spinner=”Generating recommendations...”)
def get\_recommendations(selected\_user\_id, \_model, \_mappings, \_artists\_df, num\_recs=10):
 user\_idx = \_mappings[’user\_id\_mapping’][selected\_user\_id]
 if user\_idx is None:
 st.error(f”User ID {selected\_user\_id} not found in the mapping.”)
 return pd.DataFrame(columns=[’Artist’, ‘Predicted Score’])
 
 user\_tensor = torch.LongTensor([user\_idx])
 user\_vector = \_model.user\_embedding(user\_tensor)

 all\_artist\_vectors = \_model.artist\_embedding.weight
</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">We perform a single matrix multiplication between the one user vector and the entire matrix of artist vectors. This gets us all our predictions for a given user at once.</p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> with torch.no\_grad():
 scores = torch.matmul(user\_vector, all\_artist\_vectors.T). squeeze()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We sort the scores using </span><code>torch.argsort</code><span> to get the top N, then loop over them, mapping the </span><code>artist\_model\_idx</code><span> back to the original artist ID and then to the artist’s name.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> top\_indices = torch.argsort(scores, descending=True)[:num\_recs]

 rec\_data = []
 for idx in top\_indices:
 artist\_model\_idx = idx.item()
 original\_artist\_id = \_mappings[’artist\_inv\_map’].get(artist\_model\_idx)
 if original\_artist\_id:
 artist\_name = \_artists\_df.loc[original\_artist\_id, ‘name’]
 rec\_data.append((artist\_name, scores[idx].item()))
 
 return pd.DataFrame(rec\_data, columns=[’Artist’, ‘Score’])</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>To make the visual we want to really understand collaborative filtering, we’ll add functions to simulate new data and retrain the model live. </span><code>simulate\_new\_listen</code><span> creates a new dataframe of random user-artist interactions.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">def simulate\_new\_listen(\_mappings, num\_simulations=100):
 st.write(f”Simulating {num\_simulations} new listens...”)
 all\_user\_indices = list(\_mappings[’user\_inv\_map’].keys())
 all\_artist\_indices = list(\_mappings[’artist\_inv\_map’].keys())

 sim\_users = np.random.choice(all\_user\_indices, num\_simulations)
 sim\_artists = np.random.choice(all\_artist\_indices, num\_simulations)
 
 sim\_weights = np.random.randint(50, 500, num\_simulations)

 sim\_df = pd.DataFrame({
 ‘user\_idx’: sim\_users,
 ‘artist\_idx’: sim\_artists,
 ‘weight’: sim\_weights
 })

 return sim\_df</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Now we create the </span><code>retrain\_model</code><span> function. It first checks Streamlit’s </span><code>st.session\_state</code><span> to see if a </span><code>‘retrained\_model’</code><span> already exists. If it does, we use that one. If not, then this is the first retraining so we start from the original </span><code>load\_assets()</code><span> model. This ensures that clicking the button multiple times keeps improving the same “live” model.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">def retrain\_model(new\_data): 
 st.sidebar.write(”Retraining model...”)

 if ‘retrained\_model’ in st.session\_state:
 model\_to\_retrain = st.session\_state.retrained\_model
 st.sidebar.write(”Starting from \*previously\* retrained model.”)
 else:
 model, \_, \_ = load\_assets()
 model\_to\_retrain = model
 st.sidebar.write(”Starting from \*original\* loaded model.”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Next, we prepare the new data. Just like in </span><code>train.py</code><span>, we apply the </span><code>log1p</code><span> transform and load the data into a </span><code>LastFmDataset</code><span> and a </span><code>DataLoader</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> new\_data[’weight\_log’] = np.log1p(new\_data[’weight’])
 new\_dataset = LastFmDataset(new\_data[’user\_idx’].values, new\_data[’artist\_idx’].values, new\_data[’weight\_log’].values)
 new\_loader = DataLoader(new\_dataset, batch\_size=32, shuffle=True)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We also need to define our optimizer and loss function again, pointing them at the </span><code>model\_to\_retrain</code><span>‘s parameters.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> optimizer = optim.Adam(model\_to\_retrain.parameters(), lr=0.001)
 loss\_fn = nn.MSELoss()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We run a smaller training loop, just on the new data. We set the model to </span><code>train()</code><span> mode and loop over our </span><code>new\_loader</code><span>, applying the same 5-step PyTorch training process as before.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> model\_to\_retrain.train()

 for users, artists, weights, in new\_loader:
 optimizer.zero\_grad()
 predictions = model\_to\_retrain(users, artists)
 loss = loss\_fn(predictions, weights)
 loss.backward()
 optimizer.step()
</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Finally, we set the model back to </span><code>eval()</code><span> mode and save the updated model back into </span><code>st.session\_state[’retrained\_model’]</code><span>. This replaces the old “live” model with the new, retrained one with the more up to date weights.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"> model\_to\_retrain.eval()
 st.session\_state.retrained\_model = model\_to\_retrain
 st.sidebar.success(”Retraining complete!”)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Now we create a simple app to visualize all the calculations that are happen. We’re using Streamlit to keep things simple and build it entirely in Python.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>First, the UI loads our assets. Then it checks </span><code>st.session\_state</code><span> to see if a retrained model exists. If so, we use it; otherwise, we use the original model we loaded.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">st.set\_page\_config(page\_title=”Music Recommender”, layout=”wide”)
st.title(”Interactive Music Recommender”)

model, mappings, artists\_df = load\_assets()

if ‘retrained\_model’ in st.session\_state:
 model\_to\_use = st.session\_state.retrained\_model
else:
 model\_to\_use = model</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>We create a </span><code>st.selectbox</code><span> dropdown for the user to pick a user ID.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">original\_user\_ids = list(mappings[’user\_inv\_map’].values())
st.subheader(”Select a user to see their recommendations:”)
selected\_user\_id = st.selectbox(”Select a user”, original\_user\_ids)</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>If a user is selected, we call </span><code>get\_recommendations</code><span> and display the results in a </span><code>st.table</code><span>.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">if selected\_user\_id:
 st.write(f”Top Recommendations for user: \*\*{selected\_user\_id}\*\*”)
 recs\_df = get\_recommendations(selected\_user\_id, model\_to\_use, mappings, artists\_df)
 st.table(recs\_df.set\_index(’Artist’))</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Finally, we add a sidebar with a button that, when clicked, runs the simulation and retraining. It then clears the recommendation cache and calls </span><code>st.rerun()</code><span> to refresh the app and show the new recommendations.</span></p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">st.sidebar.title(”Retraining Simulation”)
st.sidebar.write(”Simulate new user activity and retrain.”)

if st.sidebar.button(f”Simulate {SIMULATIONS} listens and retrain”):

 new\_data = simulate\_new\_listen(mappings, num\_simulations=SIMULATIONS)
 retrain\_model(new\_data)

 get\_recommendations.clear()
 st.rerun()</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">And that’s it! You’ve built a complete, end-to-end recommendation system with four files.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">To see it in action, run the following command in your terminal:</p>
<pre style="position: relative;background: #eeeeee;padding: 16px;margin: 32px 0;border-radius: 8px;box-sizing: border-box;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;"><code style="white-space: pre-wrap;font-size: 16px;line-height: 20px;font-weight: 500;">streamlit run app.py</code></code></pre>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">You’ll now be able to select any user, see their initial recommendations, and use the sidebar to simulate new data and retrain the model live to watch how its predictions change over time.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><strong>Always be (machine) learning,</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><strong>Logan</strong></p>
<p data-attrs='{"url":"https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=share&amp;utm\_campaign=email-share&amp;action=share&amp;triggerShare=true&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20","text":"Share","action":null,"class":null}' data-component-name="ButtonCreateButton" style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;margin-bottom: 0;text-align: center;cursor: pointer;border-radius: 4px;"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=share&amp;utm\_campaign=email-share&amp;action=share&amp;triggerShare=true&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20" rel="" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;cursor: pointer;border: none;border-radius: 8px;font-size: 14px;line-height: 20px;font-weight: 600;text-align: center;margin: 0;opacity: 1;outline: none;white-space: nowrap;color: #ffffff !important;text-decoration: none !important;background-color: #eb5757;padding: 12px 20px;height: auto;"><span style="color: #ffffff;text-decoration: none;">Share</span></a></p>
</div></div>
<div style="margin: 32px 0 0;width: 100%;box-sizing: border-box;border-top: 1px solid #252a35;font-size: 16px;line-height: 26px;"></div>
<div style="--image-offset-margin: -120px;font-family: Spectral,sans-serif;font-weight: 400;text-align: initial;word-break: break-word;margin-bottom: 32px;margin: 32px 0;font-size: 16px;line-height: 26px;">
<p style="color: rgb(54,55,55);margin: 0 auto 20px;text-align: center;width: 90%;line-height: 26px;font-size: 16px;margin-top: 0;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;" translated="">You're currently a free subscriber to <a href="https://substack.com/redirect/bed521e0-b8a3-4b32-b50d-7ce0bee9ee73?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="color: #eb5757;text-decoration: none;">Machine Learning for Software Engineers</a>. For the full experience, <a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL3N1YnNjcmliZT91dG1fc291cmNlPXBvc3QmdXRtX2NhbXBhaWduPWVtYWlsLWNoZWNrb3V0Jm5leHQ9aHR0cHMlM0ElMkYlMkZtbGZvcnN3ZXMuY29tJTJGcCUyRmNvbGxhYm9yYXRpdmUtZmlsdGVyaW5nJnI9NnE2ZWdsJnRva2VuPWV5SjFjMlZ5WDJsa0lqbzBNRFkzTmpVM05Ea3NJbWxoZENJNk1UYzJNamcyT1RreE1Dd2laWGh3SWpveE56WTFORFl4T1RFd0xDSnBjM01pT2lKd2RXSXRNVGMwTkRFM09TSXNJbk4xWWlJNkltTm9aV05yYjNWMEluMC5hdnhoazByME16WVJnWmRKWWNTekpkd2tpaXBudm93VW94dTl1cG5jMF9rIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.3owYekc7J3etlWzqcZu3wFNPD38TLz2IBCxwY2m2o-M?&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=postcta" style="color: #eb5757;text-decoration: none;">upgrade your subscription.</a></span></p>
<p style="color: rgb(54,55,55);margin: 0 auto 20px;width: 90%;line-height: 26px;font-size: 16px;margin-bottom: 0;text-align: center;margin-left: auto;margin-right: auto;"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL3N1YnNjcmliZT91dG1fc291cmNlPXBvc3QmdXRtX2NhbXBhaWduPWVtYWlsLWNoZWNrb3V0Jm5leHQ9aHR0cHMlM0ElMkYlMkZtbGZvcnN3ZXMuY29tJTJGcCUyRmNvbGxhYm9yYXRpdmUtZmlsdGVyaW5nJnI9NnE2ZWdsJnRva2VuPWV5SjFjMlZ5WDJsa0lqbzBNRFkzTmpVM05Ea3NJbWxoZENJNk1UYzJNamcyT1RreE1Dd2laWGh3SWpveE56WTFORFl4T1RFd0xDSnBjM01pT2lKd2RXSXRNVGMwTkRFM09TSXNJbk4xWWlJNkltTm9aV05yYjNWMEluMC5hdnhoazByME16WVJnWmRKWWNTekpkd2tpaXBudm93VW94dTl1cG5jMF9rIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.3owYekc7J3etlWzqcZu3wFNPD38TLz2IBCxwY2m2o-M?&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=postcta" role="button" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;cursor: pointer;border: none;height: 40px;border-radius: 8px;font-size: 14px;line-height: 20px;font-weight: 600;text-align: center;padding: 10px 20px;margin: 0;opacity: 1;outline: none;white-space: nowrap;color: #ffffff !important;text-decoration: none !important;background-color: #eb5757;">Upgrade to paid</a></p>
</div>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="border-top: 1px solid rgb(0,0,0,.1);border-bottom: 1px solid rgb(0,0,0,.1);min-width: 100%;" width="100%"><tbody>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="margin:0 auto;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;isFreemail=true&amp;submitLike=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwicmVhY3Rpb24iOiLinaQiLCJpYXQiOjE3NjI4Njk5MTAsImV4cCI6MTc2NTQ2MTkxMCwiaXNzIjoicHViLTE3NDQxNzkiLCJzdWIiOiJyZWFjdGlvbiJ9.9nhwnhUeYT9WZh3iZ4tLu53-WXg5OBzr98xKSTMIRms&amp;utm\_medium=email&amp;utm\_campaign=email-reaction&amp;r=6q6egl" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!PeVs!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Like</span></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1744179&amp;post\_id=178561311&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3ODU2MTMxMSwiaWF0IjoxNzYyODY5OTEwLCJleHAiOjE3NjU0NjE5MTAsImlzcyI6InB1Yi0xNzQ0MTc5Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.9Fr9JKV\_fQzpiADJJXpQ6PyLryMy\_c79K3AFegnev20&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!x1tS!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideComments%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Comment</span></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9vcGVuLnN1YnN0YWNrLmNvbS9wdWIvc29jaWV0eXNiYWNrZW5kL3AvY29sbGFib3JhdGl2ZS1maWx0ZXJpbmc\_dXRtX3NvdXJjZT1zdWJzdGFjayZ1dG1fbWVkaXVtPWVtYWlsJnV0bV9jYW1wYWlnbj1lbWFpbC1yZXN0YWNrLWNvbW1lbnQmYWN0aW9uPXJlc3RhY2stY29tbWVudCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09EVTJNVE14TVN3aWFXRjBJam94TnpZeU9EWTVPVEV3TENKbGVIQWlPakUzTmpVME5qRTVNVEFzSW1semN5STZJbkIxWWkweE56UTBNVGM1SWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuOUZyOUpLVl9mUXpwaUFESkpYcFE2UHlMcnlNeV9jNzlLM0FGZWduZXYyMCIsInAiOjE3ODU2MTMxMSwicyI6MTc0NDE3OSwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjI4Njk5MTAsImV4cCI6MjA3ODQ0NTkxMCwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.CBVTBFy6IkXmkon3nthkoiqeJg8YymkwUom5yYFVw1M?&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!5EGt!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Restack</span></a></td></tr></tbody></table></td>
</tr></tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr></tr></tbody></table></td>
</tr></tbody></table></td></tr>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
</tbody></table>
<div style="color: rgb(119,119,119);text-align: center;font-size: 16px;line-height: 26px;padding: 24px0;">
<div style="font-size: 16px;line-height: 26px;padding-bottom: 24px"><p style="list-style: none;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;font-size: 12px;line-height: 16px;margin: 0;color: rgb(119,119,119);text-decoration: unset;">© 2025 <span>Logan Thorneloe</span><br/>548 Market Street PMB 72296, San Francisco, CA 94104 <br/><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9tbGZvcnN3ZXMuY29tL2FjdGlvbi9kaXNhYmxlX2VtYWlsP3Rva2VuPWV5SjFjMlZ5WDJsa0lqbzBNRFkzTmpVM05Ea3NJbkJ2YzNSZmFXUWlPakUzT0RVMk1UTXhNU3dpYVdGMElqb3hOell5T0RZNU9URXdMQ0psZUhBaU9qRTNPVFEwTURVNU1UQXNJbWx6Y3lJNkluQjFZaTB4TnpRME1UYzVJaXdpYzNWaUlqb2laR2x6WVdKc1pWOWxiV0ZwYkNKOS5yRS1jTURIYmhBZHNhei1SVUVfZjJrejg2TlduQ1BNbEtEcmp1ZkR3WndrIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.wP9aDhW4cBOjM4g0I0HWbWrNbXrHERKC-1MakOCFT6E?" style="color: #eb5757;text-decoration: none;"><span style="color: rgb(119,119,119);text-decoration: underline;">Unsubscribe</span></a></p></div>
<p style="padding: 0 24px;font-size: 12px;line-height: 20px;margin: 0;color: rgb(119,119,119);font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;margin-top: 0;"><a href="https://substack.com/redirect/1cb40c0a-3d93-4657-abfb-22add62c5355?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="color: #eb5757;text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Get the app" height="40" src="https://substackcdn.com/image/fetch/%24s\_!IzGP!,w\_262,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!DIki!,w\_131,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button.png, https://substackcdn.com/image/fetch/$s\_!IzGP!,w\_262,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!QWua!,w\_393,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="131"/></a><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zdWJzdGFjay5jb20vc2lnbnVwP3V0bV9zb3VyY2U9c3Vic3RhY2smdXRtX21lZGl1bT1lbWFpbCZ1dG1fY29udGVudD1mb290ZXImdXRtX2NhbXBhaWduPWF1dG9maWxsZWQtZm9vdGVyJmZyZWVTaWdudXBFbWFpbD1pbWVvYnZua0BsaWJyYXJ5LnJlYWR3aXNlLmlvJnI9NnE2ZWdsIiwicCI6MTc4NTYxMzExLCJzIjoxNzQ0MTc5LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoyMDc4NDQ1OTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.Es8195fpbmLRo\_JjFlFSuy55UHZzP3cNs0c06XYP7S0?" style="color: #eb5757;text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Start writing" height="40" src="https://substackcdn.com/image/fetch/%24s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!wgfj!,w\_135,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button.png, https://substackcdn.com/image/fetch/$s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!KjtY!,w\_405,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="135"/></a></p>
</div>
</div></td>
<td></td>
</tr>
</tbody></table>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjUxMTExMTQwMzE0LjMuODA1OWZkYmY2NGViYTg1MEBtZy1kMC5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMC5zdWJzdGFjay5jb20iLCJwIjoxNzg1NjEzMTEsInQiOiJuZXdzbGV0dGVyIiwiYSI6ImV2ZXJ5b25lIiwicyI6MTc0NDE3OSwiYyI6InBvc3QiLCJmIjp0cnVlLCJwb3NpdGlvbiI6ImJvdHRvbSIsImlhdCI6MTc2Mjg2OTkxMCwiZXhwIjoxNzY1NDYxOTEwLCJpc3MiOiJwdWItMCIsInN1YiI6ImVvIn0.dCvx\_KxnVKQzCmP1AgpQHQxbqYGuvCIy1e5BLzWrsFQ" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><img alt="" height="1" src="https://email.mg-d0.substack.com/o/eJxEkEvO4yAQBk\_zsxsLMA97wVmsBppMKwYiHol8-1Emkf5eVkul0hdg4K22yz1qHyw6s0LSkaET1sjN7LswDDPQedywYIOB8YDx--WSc\_bXobZrksmKFDYljdbKmrRJuwEmEZNl5CSXWrxP8VWoZV02rvcUfTIKPWya\_yieb38iX\_r0fUC4L6FmRv1IDf8nuNEmsnfoATMSloAOn9iuWr6YohN200asQnzIuB7oCr76iWNgY4\_pj1BznoXGdWABf2L8iqc\_KcCgWj4ipYTdWXOUsfpnuf8ofpJv0K6lIcQXdVyosj59rBmouF4D4bi6h3DHEtn4rDo7trdRcWONtmpnTyf\_BQAA\_\_\_gW33R" width="1"/>
</div>
