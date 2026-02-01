# Cameron R. Wolfe, Ph.D., Sebastian Raschka, PhD, and Devansh posted new notes

![rw-book-cover](https://substackcdn.com/icons/substack/apple-touch-icon-1024x1024.png)

## Metadata
- Author: [[Substack]]
- Full Title: Cameron R. Wolfe, Ph.D., Sebastian Raschka, PhD, and Devansh posted new notes
- Category: #articles
- Summary: Researchers discuss if large language models learn new skills during reinforcement learning. The answer depends on the base model's strength and the tasks used in training. If tasks are complex, models may learn new abilities; otherwise, they mostly improve what they already know.
- URL: mailto:reader-forwarded-email/adb1cc93df4a907aab032731fa8fca4f

## Full Document
![Substack](https://substackcdn.com/image/fetch/$s_!Rt8r!,w_40,h_40,c_fill,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2)##### Cameron R. Wolfe, Ph.D., Sebastian Raschka, PhD, and Devansh posted new notes

[![](https://substackcdn.com/image/fetch/$s_!iOMz!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3)

![](https://substackcdn.com/image/fetch/$s_!jUgr!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdcabb40d-0160-46a4-ad4f-55b486a11ee0_1024x1024.jpeg)

Logan Thorneloe liked![](https://substackcdn.com/image/fetch/$s_!VC2M!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8_1242x1595.jpeg)

Cameron R. Wolfe, Ph.D.

![](https://substackcdn.com/image/fetch/$s_!uCNK!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6)You follow6d

There's a lot of ongoing discussion on whether LLMs actually learn new capabilities from RL. I think part of the problem here is that the answer to this question has an external dependence on: 1. The quality / capabilities of the base model. 2. The data / task mixture for RL training. It seems like models are capable of learning new capabilities during RL if it is necessary, but the model may not need to learn new capabilities during RL depending on the above two factors. For this reason, analysis on this topic is variable and nuanced. As base models get better, RL may be reinforcing existing capabilities rather than learning new capabilities. Similarly, if we add a new, highly-complex task / environment into our RL setup the model may be forced to learn new skills during RL. One of my favorite illustrations of this point is from this paper: https://arxiv.org/abs/2512.01970 A synthetic compositional reasoning task is created that is based upon a set number of…Read More ![](https://substackcdn.com/image/fetch/$s_!ITqs!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2)![](https://substackcdn.com/image/fetch/$s_!0eBN!,w_200,h_200,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2a1a7076-41f6-4641-b663-1e8e54ff44c4_1199x435.png)

![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)11

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3) 

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)2

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@cwolferesearch/note/c-204630749?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!iOMz!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3)

![](https://substackcdn.com/image/fetch/$s_!aGhb!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94_1008x1008.png)

Sergei Polevikov liked![](https://substackcdn.com/image/fetch/$s_!CfW_!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F61f4c017-506f-4e9b-a24f-76340dad0309_800x800.jpeg)

Sebastian Raschka, PhD

![](https://substackcdn.com/image/fetch/$s_!yL03!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeIcon%3Fv%3D4%26height%3D32%26fill%3D%2523FF6719%26strokeWidth%3D3.6)You follow5d

Workful weekend! Running lots of experiments for a Tips & Tricks follow-up to my GRPO from-scratch…Read More ![](https://substackcdn.com/image/fetch/$s_!ITqs!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2)![](https://substackcdn.com/image/fetch/$s_!bUeF!,w_200,h_200,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7d0b0c5f-ed0a-4e60-8e78-1394e94555cb_1632x1112.png)

![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)43

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)2

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)4

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@rasbt/note/c-205100943?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!iOMz!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3)

![](https://substackcdn.com/image/fetch/$s_!jUgr!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdcabb40d-0160-46a4-ad4f-55b486a11ee0_1024x1024.jpeg)

Logan Thorneloe liked![](https://substackcdn.com/image/fetch/$s_!0X66!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F48081c70-8afa-41e3-a44e-b0f917bc7577_1200x1600.jpeg)

Devansh

![](https://substackcdn.com/image/fetch/$s_!uCNK!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6)You follow5d

Not to be too preachy, but it’s quite disappointing how none of the AI creators online speak out against the many ways the tech industry is using AI to build a techno-police state or encroach on workers’ rights. I get the whole, “I don’t want to be political” thing but not fighting against an unjust status…Read More ![](https://substackcdn.com/image/fetch/$s_!ITqs!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2)![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)25

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)5

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)3

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@chocolatemilkcultleader/note/c-205164978?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!nmag!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fca736a83-f5a1-4563-ac6c-c09a9e6fa351_800x800.png)

![](https://substackcdn.com/image/fetch/$s_!RihO!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8fedcdfb-e137-4f6a-9089-a46add6c6242_500x500.jpeg)

![](https://substackcdn.com/image/fetch/$s_!aGhb!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94_1008x1008.png)

![](https://substackcdn.com/image/fetch/$s_!59iK!,w_48,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FDotDotDotCircleIcon%3Fv%3D4%26height%3D48%26strokeWidth%3D3.6)

See more notes in the Substack app](https://open.substack.com/notes?utm_source=feed-email-digest&utm_campaign=open-in-app&redirect=app-store-no-desktop)© 2026 Substack Inc.  
548 Market Street PMB 72296, San Francisco, CA 94104   
[Unsubscribe](https://substack.com/api/v1/email/notification/unsubscribe?token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInRvcGljIjoicmVhZGVyX3B1YmxpY2F0aW9uX3JlY29tbWVuZGF0aW9uIiwiaWF0IjoxNzY5ODM2NzQ3LCJleHAiOjE4MDEzNzI3NDcsImlzcyI6InB1Yi0wIiwic3ViIjoibm90aWZpY2F0aW9uLXVuc3Vic2NyaWJlIn0.E8uSf1GkAFh0yQC31wLLMxgdm4rShnVFLeAGJHyfbMY)

[![Start writing](https://substackcdn.com/image/fetch/$s_!LkrL!,w_270,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png)](https://substack.com/signup?utm_source=substack&utm_medium=email&utm_content=footer&utm_campaign=autofilled-footer&freeSignupEmail=imeobvnk@library.readwise.io&r=6q6egl)

991

<div>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjYwMTMxMDUxOTA2LjMuZDhmMWU1MjAyOTRhOTE2OS4ycDhnaTRleUBtZzIuc3Vic3RhY2suY29tPiIsInUiOjQwNjc2NTc0OSwiciI6ImltZW9idm5rQGxpYnJhcnkucmVhZHdpc2UuaW8iLCJkIjoibWcyLnN1YnN0YWNrLmNvbSIsInAiOm51bGwsInQiOm51bGwsImEiOm51bGwsInMiOm51bGwsImMiOiJmZWVkLWRpZ2VzdC1lbWFpbCIsImYiOnRydWUsInBvc2l0aW9uIjoidG9wIiwiaWF0IjoxNzY5ODM2NzQ3LCJleHAiOjE3NzI0Mjg3NDcsImlzcyI6InB1Yi0wIiwic3ViIjoiZW8ifQ.LK3IZELVdqVKYQhwpRw3t37NpBG0IpmlArvQUu7G2ao" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td style="color:transparent;"> </td>
<td align="center" width="468"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><div draggable="false" style="text-decoration: unset;list-style: none;display: flex;position: relative;"><div style="text-decoration: unset;list-style: none;border-radius: 8px;display: flex;background-color: rgb(255,255,255);overflow: hidden;box-sizing: border-box;width: 40px;height: 40px"><picture style="text-decoration: unset;list-style: none;display: contents;"><source sizes="40px" srcset="https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_40,h\_40,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 40w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_80,h\_80,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 80w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_120,h\_120,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 120w" type="image/webp"/><img alt="Substack" draggable="false" sizes="40px" src="https://substackcdn.com/image/fetch/%24s\_!Rt8r!,w\_40,h\_40,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2" srcset="https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_40,h\_40,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 40w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_80,h\_80,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 80w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_120,h\_120,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 120w" style="text-decoration: unset;list-style: none;width: 40px;height: 40px;max-width: 550px;border: none !important;vertical-align: middle;"/></picture></div></div></td></tr>
<tr height="16"><td></td></tr>
<tr><td><h3 style="-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;color: unset;list-style: none;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 700;margin: 0;line-height: 28px;font-size: 24px;text-decoration: unset;">Cameron R. Wolfe, Ph.D., Sebastian Raschka, PhD, and Devansh posted new notes</h3></td></tr>
<tr height="16"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td>
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@cwolferesearch/note/c-204630749?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"><div style="text-decoration: unset;list-style: none;padding-left: 44px;padding-bottom: 14px"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!iOMz!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="16"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><img height="20" src="https://substackcdn.com/image/fetch/%24s\_!jUgr!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdcabb40d-0160-46a4-ad4f-55b486a11ee0\_1024x1024.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 20px;height: 20px;min-width: 20px;min-height: 20px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="20"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Logan Thorneloe liked</div></td>
</tr></tbody></table></div></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!VC2M!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8\_1242x1595.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width: 12px" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Cameron R. Wolfe, Ph.D.</span></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!uCNK!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">6d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">There's a lot of ongoing discussion on whether LLMs actually learn new capabilities from RL. I think part of the problem here is that the answer to this question has an external dependence on: 1. The quality / capabilities of the base model. 2. The data / task mixture for RL training. It seems like models are capable of learning new capabilities during RL if it is necessary, but the model may not need to learn new capabilities during RL depending on the above two factors. For this reason, analysis on this topic is variable and nuanced. As base models get better, RL may be reinforcing existing capabilities rather than learning new capabilities. Similarly, if we add a new, highly-complex task / environment into our RL setup the model may be forced to learn new skills during RL. One of my favorite illustrations of this point is from this paper: https://arxiv.org/abs/2512.01970 A synthetic compositional reasoning task is created that is based upon a set number of…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!ITqs!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2" style="max-width: 550px;border: none;vertical-align: text-bottom" width="16"/>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><img src="https://substackcdn.com/image/fetch/%24s\_!0eBN!,w\_200,h\_200,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2a1a7076-41f6-4641-b663-1e8e54ff44c4\_1199x435.png" style="text-decoration: unset;list-style: none;border-radius: 8px;width: 100px;max-width: 550px;border: none;vertical-align: middle;max-height: 100px;object-fit: cover;margin: 0px"/></td></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">11</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px"> </span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!j45G!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">2</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!wv04!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px"> </span>
</td>
<td></td>
</tr></tbody></table></td></tr>
</tbody></table></td>
</tr></tbody></table>
</td></tr>
<tr height="20"><td></td></tr>
<tr><td>
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@rasbt/note/c-205100943?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"><div style="text-decoration: unset;list-style: none;padding-left: 44px;padding-bottom: 14px"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!iOMz!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="16"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><img height="20" src="https://substackcdn.com/image/fetch/%24s\_!aGhb!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94\_1008x1008.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 20px;height: 20px;min-width: 20px;min-height: 20px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="20"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Sergei Polevikov liked</div></td>
</tr></tbody></table></div></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!CfW\_!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F61f4c017-506f-4e9b-a24f-76340dad0309\_800x800.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width: 12px" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Sebastian Raschka, PhD</span></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!yL03!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeIcon%3Fv%3D4%26height%3D32%26fill%3D%2523FF6719%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">5d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Workful weekend! Running lots of experiments for a Tips &amp; Tricks follow-up to my GRPO from-scratch…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!ITqs!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2" style="max-width: 550px;border: none;vertical-align: text-bottom" width="16"/>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><img src="https://substackcdn.com/image/fetch/%24s\_!bUeF!,w\_200,h\_200,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F7d0b0c5f-ed0a-4e60-8e78-1394e94555cb\_1632x1112.png" style="text-decoration: unset;list-style: none;border-radius: 8px;width: 100px;max-width: 550px;border: none;vertical-align: middle;max-height: 100px;object-fit: cover;margin: 0px"/></td></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">43</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">2</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!j45G!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">4</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!wv04!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px"> </span>
</td>
<td></td>
</tr></tbody></table></td></tr>
</tbody></table></td>
</tr></tbody></table>
</td></tr>
<tr height="20"><td></td></tr>
<tr><td>
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@chocolatemilkcultleader/note/c-205164978?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"><div style="text-decoration: unset;list-style: none;padding-left: 44px;padding-bottom: 14px"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!iOMz!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="16"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><img height="20" src="https://substackcdn.com/image/fetch/%24s\_!jUgr!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdcabb40d-0160-46a4-ad4f-55b486a11ee0\_1024x1024.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 20px;height: 20px;min-width: 20px;min-height: 20px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="20"/></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Logan Thorneloe liked</div></td>
</tr></tbody></table></div></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!0X66!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F48081c70-8afa-41e3-a44e-b0f917bc7577\_1200x1600.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width: 12px" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Devansh</span></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!uCNK!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width: 6px" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">5d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Not to be too preachy, but it’s quite disappointing how none of the AI creators online speak out against the many ways the tech industry is using AI to build a techno-police state or encroach on workers’ rights. I get the whole, “I don’t want to be political” thing but not fighting against an unjust status…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!ITqs!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideChevronsRight%3Fv%3D4%26height%3D32%26stroke%3Drgb(0%252C%2520118%252C%2520255)%26strokeWidth%3D2" style="max-width: 550px;border: none;vertical-align: text-bottom" width="16"/>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">25</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">5</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!j45G!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">3</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!wv04!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px"> </span>
</td>
<td></td>
</tr></tbody></table></td></tr>
</tbody></table></td>
</tr></tbody></table>
</td></tr>
</tbody></table></td></tr>
<tr height="18"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="box-sizing: border-box;width: 100%;min-height: 40px;padding-left: 0;padding-right: 0;" width="auto"><tbody><tr><td align="center" style="box-sizing: border-box;width: 100%;min-height: 40px;padding-left: 0;padding-right: 0;border-radius: 8px;background-color: rgb(255,103,25);">
<a href="https://open.substack.com/notes?utm\_source=feed-email-digest&amp;utm\_campaign=open-in-app&amp;redirect=app-store-no-desktop" style="box-sizing: border-box;width: 468px;min-height: 40px;padding-left: 0;padding-right: 0;display: block!important;text-decoration: none;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-size: 14px;font-weight: 600;letter-spacing: -.15px;border-radius: 8px;padding: 12px 24px;line-height: 1;color: rgb(255,255,255);border: none;"></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="padding-left:12px;padding-right:12px;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!nmag!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fca736a83-f5a1-4563-ac6c-c09a9e6fa351\_800x800.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!RihO!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8fedcdfb-e137-4f6a-9089-a46add6c6242\_500x500.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!aGhb!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94\_1008x1008.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><img alt="" height="24" src="https://substackcdn.com/image/fetch/%24s\_!59iK!,w\_48,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FDotDotDotCircleIcon%3Fv%3D4%26height%3D48%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 24px" width="24"/></td>
</tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;color: rgb(255,255,255);text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;" translated="">See more notes in the Substack app</div></td>
</tr></tbody></table>
</td></tr></tbody></table></td></tr>
</tbody></table></td></tr>
<tr height="16"><td></td></tr>
<tr><td><div style="color: rgb(119,119,119);text-align: center;padding: 24px0;">
<div style="padding-bottom:24px;"><p style="list-style: none;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;line-height: 16px;margin: 0;color: rgb(119,119,119);font-size: 12px;text-decoration: unset;">© 2026 <span>Substack Inc.</span><br/>548 Market Street PMB 72296, San Francisco, CA 94104 <br/><a href="https://substack.com/api/v1/email/notification/unsubscribe?token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInRvcGljIjoicmVhZGVyX3B1YmxpY2F0aW9uX3JlY29tbWVuZGF0aW9uIiwiaWF0IjoxNzY5ODM2NzQ3LCJleHAiOjE4MDEzNzI3NDcsImlzcyI6InB1Yi0wIiwic3ViIjoibm90aWZpY2F0aW9uLXVuc3Vic2NyaWJlIn0.E8uSf1GkAFh0yQC31wLLMxgdm4rShnVFLeAGJHyfbMY" style="text-decoration: underline;color: rgb(119,119,119);"><span style="color: rgb(119,119,119);text-decoration: underline;">Unsubscribe</span></a></p></div>
<p style="padding: 0 24px;line-height: 20px;margin: 0;color: rgb(119,119,119);font-size: 12px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;margin-top: 0;"><a href="https://substack.com/signup?utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=footer&amp;utm\_campaign=autofilled-footer&amp;freeSignupEmail=imeobvnk@library.readwise.io&amp;r=6q6egl" style="color: rgb(119,119,119);text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Start writing" height="40" src="https://substackcdn.com/image/fetch/%24s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!wgfj!,w\_135,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button.png, https://substackcdn.com/image/fetch/$s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!KjtY!,w\_405,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="135"/></a></p>
</div></td></tr>
<tr height="16"><td></td></tr>
<tr><td><div style="height: 1px;color: rgba(254, 254, 254, 0.01);overflow: hidden;">991</div></td></tr>
</tbody></table></td>
<td style="color:transparent;"> </td>
</tr></tbody></table>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjYwMTMxMDUxOTA2LjMuZDhmMWU1MjAyOTRhOTE2OS4ycDhnaTRleUBtZzIuc3Vic3RhY2suY29tPiIsInUiOjQwNjc2NTc0OSwiciI6ImltZW9idm5rQGxpYnJhcnkucmVhZHdpc2UuaW8iLCJkIjoibWcyLnN1YnN0YWNrLmNvbSIsInAiOm51bGwsInQiOm51bGwsImEiOm51bGwsInMiOm51bGwsImMiOiJmZWVkLWRpZ2VzdC1lbWFpbCIsImYiOnRydWUsInBvc2l0aW9uIjoiYm90dG9tIiwiaWF0IjoxNzY5ODM2NzQ3LCJleHAiOjE3NzI0Mjg3NDcsImlzcyI6InB1Yi0wIiwic3ViIjoiZW8ifQ.RJdLu2hF1WzAUow9PkDeqNzopWSfXHDWy2lfAiLGeCQ" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><img alt="" height="1" src="https://email.mg2.substack.com/o/eJxskMtqwzAURL8m2kXoZT0W-hZzLV27l0RWkOQY\_31poNBFlzOHgeEkGLjVdsUVMd8zbdjHHQvQk-VosvSTZxils8Fr64xjHzZvuGODgXmG8YcKJ9hXTC5k0Fpl77Q2K2JAhwhKCAerT45RVEJZIbUUkwzCcs2zXyVOSqhgIEgbuHr5jQxeNyPKpng\_lj4gPXiqhVGf14afJ3G0A9leB62UYFDd53G9MDaEjG1-Hcvzt2-Yaim4509kLVLBurz3x82IJy0N2sV\_Zid15FRZP5ZcC9Aez\_Nk4x9DR8c2U45GWGcnZwJ7R\_UdAAD\_\_1bycDA" width="1"/>
</div>
