# Sebastian Raschka, PhD, Nathan Lambert, and Devansh posted new notes

![rw-book-cover](https://substackcdn.com/icons/substack/apple-touch-icon-1024x1024.png)

## Metadata
- Author: [[Substack]]
- Full Title: Sebastian Raschka, PhD, Nathan Lambert, and Devansh posted new notes
- Category: #articles
- Summary: Two new large language models from India, Sarvam 30B and 105B, were released with advanced attention techniques. The bigger Sarvam 105B matches top models in performance but uses a more complex attention method. Experts note that many leading models perform similarly, so companies focus on pricing and strategies to stand out.
- URL: mailto:reader-forwarded-email/ca4a004006255105a189174587f87ad0

## Full Document
![Substack](https://substackcdn.com/image/fetch/$s_!Rt8r!,w_40,h_40,c_fill,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2)##### Sebastian Raschka, PhD, Nathan Lambert, and Devansh posted new notes

[![](https://substackcdn.com/image/fetch/$s_!iOMz!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3)

![](https://substackcdn.com/image/fetch/$s_!aGhb!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94_1008x1008.png)

Sergei Polevikov liked![](https://substackcdn.com/image/fetch/$s_!CfW_!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F61f4c017-506f-4e9b-a24f-76340dad0309_800x800.jpeg)

Sebastian Raschka, PhD

![](https://substackcdn.com/image/fetch/$s_!yL03!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeIcon%3Fv%3D4%26height%3D32%26fill%3D%2523FF6719%26strokeWidth%3D3.6)You follow6d

While waiting for DeepSeek V4 we got two very strong open-weight LLMs from India yesterday. There are two size flavors, Sarvam 30B and Sarvam 105B model (both reasoning models). Interestingly, the smaller 30B model uses “classic” Grouped Query Attention (GQA), whereas the larger 105B variant switched to DeepSeek-style Multi-Head Latent Attention (MLA). As I wrote about in my analyses before, both are popular attention variants to reduce KV cache size (the longer the context, the more you save compared to regular attention). MLA is more complicated to implement, but it can give you better modeling performance if we go by the ablation studies in the 2024 DeepSeek V2 paper (as far as I know, this is still the most recent apples-to-apples comparison). Speaking of modeling performance, the 105B model is on par with LLMs of similar size: gpt-oss 120B and Qwen3-Next (80B…Read More ![](https://substackcdn.com/image/fetch/$s_!v1hC!,w_200,h_200,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F273f9602-842d-4512-859c-6a47d17bbf71_5789x5861.png)

![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)112

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)4

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)7

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@rasbt/note/c-224400542?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!iOMz!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3)

![](https://substackcdn.com/image/fetch/$s_!VC2M!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8_1242x1595.jpeg)

Cameron R. Wolfe, Ph.D. liked![](https://substackcdn.com/image/fetch/$s_!RihO!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8fedcdfb-e137-4f6a-9089-a46add6c6242_500x500.jpeg)

Nathan Lambert

![](https://substackcdn.com/image/fetch/$s_!uCNK!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6)You follow6d

Touch grass (and mud and…Read More ![](https://substackcdn.com/image/fetch/$s_!yyrO!,w_200,h_200,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6c6328dd-0006-467c-9519-1ac6b84f25c5_3088x2316.heic)

![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)75

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)2

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3) 

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@natolambert/note/c-224489071?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!0X66!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F48081c70-8afa-41e3-a44e-b0f917bc7577_1200x1600.jpeg)

Devansh

![](https://substackcdn.com/image/fetch/$s_!uCNK!,w_32,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6)You follow6d

MiniMax scores 80.2% on SWE-Bench at $0.30/M tokens. Claude Opus scores 80.8% at $5.00. You're paying 19x more for six-tenths of a percentage point that NIST says might be noise. But there's more. Ten frontier models launched in February. The top five cluster within 2.5 points. For pattern-matching workloads, the models are functionally interchangeable . So how do labs actually differentiate their offering and stand out against the competition? I spent a few weeks digging through the data for this month's report and three strategies stood out. Google is doing something clever that I think is underappreciated. Flash handles the cheap high-volume work, you burn through tokens, your credits accumulate, your pricing tier rises. By the time you actually need a premium model Gemini Pro is just sitting there at $2/M. The commodity model isn't the product, it's the on-ramp. Their cloud margins nearly doubled in a year so…Read More ![](https://substackcdn.com/image/fetch/$s_!6UaQ!,w_200,h_200,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0e53c4bc-2c79-45d0-ae23-009984711c70_4500x2700.png)

![](https://substackcdn.com/image/fetch/$s_!F4ic!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3)18

![](https://substackcdn.com/image/fetch/$s_!CRYW!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)2

![](https://substackcdn.com/image/fetch/$s_!j45G!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)3

![](https://substackcdn.com/image/fetch/$s_!wv04!,w_28,c_scale,f_png,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3)](https://substack.com/@chocolatemilkcultleader/note/c-224572530?utm_source=feed-email-digest)[![](https://substackcdn.com/image/fetch/$s_!VC2M!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8_1242x1595.jpeg)

![](https://substackcdn.com/image/fetch/$s_!mcL6!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3403a50f-4e67-40d2-aa6f-a8d845f19c1c_480x480.png)

![](https://substackcdn.com/image/fetch/$s_!aGhb!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94_1008x1008.png)

See more notes in the Substack app](https://open.substack.com/notes?utm_source=feed-email-digest&utm_campaign=open-in-app&redirect=app-store-no-desktop)© 2026 Substack Inc.  
548 Market Street PMB 72296, San Francisco, CA 94104   
[Unsubscribe](https://substack.com/api/v1/email/notification/unsubscribe?token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInRvcGljIjoicmVhZGVyX3B1YmxpY2F0aW9uX3JlY29tbWVuZGF0aW9uIiwiaWF0IjoxNzczNDQ4NzEzLCJleHAiOjE4MDQ5ODQ3MTMsImlzcyI6InB1Yi0wIiwic3ViIjoibm90aWZpY2F0aW9uLXVuc3Vic2NyaWJlIn0.Ty8jOzATVnIAmrmsqGkKzRc_BRuIcsd01t9apSGk_dU)

[![Start writing](https://substackcdn.com/image/fetch/$s_!LkrL!,w_270,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png)](https://substack.com/signup?utm_source=substack&utm_medium=email&utm_content=footer&utm_campaign=autofilled-footer&freeSignupEmail=imeobvnk@library.readwise.io&r=6q6egl)

935

<div>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjYwMzE0MDAzODMyLjMuZDhmMWU1MjAyOTRhOTE2OS5xbG5lMGJha0BtZy1kMS5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMS5zdWJzdGFjay5jb20iLCJwIjpudWxsLCJ0IjpudWxsLCJhIjpudWxsLCJzIjpudWxsLCJjIjoiZmVlZC1kaWdlc3QtZW1haWwiLCJmIjp0cnVlLCJwb3NpdGlvbiI6InRvcCIsImlhdCI6MTc3MzQ0ODcxMywiZXhwIjoxNzc2MDQwNzEzLCJpc3MiOiJwdWItMCIsInN1YiI6ImVvIn0.QytRjBS4T9H91G30KchXzyoUUU1wcRpYHlAkBGMMaVY" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td style="color:transparent;"> </td>
<td align="center" width="468"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><div draggable="false" style="text-decoration: unset;list-style: none;display: flex;position: relative;"><div style="text-decoration: unset;list-style: none;border-radius: 8px;display: flex;background-color: rgb(255,255,255);overflow: hidden;box-sizing: border-box;width: 40px;height: 40px"><picture style="text-decoration: unset;list-style: none;display: contents;"><img alt="Substack" draggable="false" sizes="40px" src="https://substackcdn.com/image/fetch/%24s\_!Rt8r!,w\_40,h\_40,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2" srcset="https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_40,h\_40,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 40w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_80,h\_80,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 80w, https://substackcdn.com/image/fetch/$s\_!Rt8r!,w\_120,h\_120,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Fsubstack-system-email-align-left.png%3Fv%3D2 120w" style="text-decoration: unset;list-style: none;max-width: 550px;border: none;vertical-align: middle;object-fit: cover;width: 40px;height: 40px"/></picture></div></div></td></tr>
<tr height="16"><td></td></tr>
<tr><td><h3 style="-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;color: unset;list-style: none;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 700;margin: 0;line-height: 28px;font-size: 24px;text-decoration: unset;">Sebastian Raschka, PhD, Nathan Lambert, and Devansh posted new notes</h3></td></tr>
<tr height="16"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td>
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@rasbt/note/c-224400542?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"><div style="text-decoration: unset;list-style: none;padding-left: 44px;padding-bottom: 14px"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!iOMz!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="16"/></td>
<td style="min-width:8px;" width="8"></td>
<td style="vertical-align:middle;"><img height="20" src="https://substackcdn.com/image/fetch/%24s\_!aGhb!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94\_1008x1008.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 20px;height: 20px;min-width: 20px;min-height: 20px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="20"/></td>
<td style="min-width:8px;" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Sergei Polevikov liked</div></td>
</tr></tbody></table></div></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!CfW\_!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F61f4c017-506f-4e9b-a24f-76340dad0309\_800x800.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width:12px;" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Sebastian Raschka, PhD</span></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!yL03!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeIcon%3Fv%3D4%26height%3D32%26fill%3D%2523FF6719%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">6d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">While waiting for DeepSeek V4 we got two very strong open-weight LLMs from India yesterday. There are two size flavors, Sarvam 30B and Sarvam 105B model (both reasoning models). Interestingly, the smaller 30B model uses “classic” Grouped Query Attention (GQA), whereas the larger 105B variant switched to DeepSeek-style Multi-Head Latent Attention (MLA). As I wrote about in my analyses before, both are popular attention variants to reduce KV cache size (the longer the context, the more you save compared to regular attention). MLA is more complicated to implement, but it can give you better modeling performance if we go by the ablation studies in the 2024 DeepSeek V2 paper (as far as I know, this is still the most recent apples-to-apples comparison). Speaking of modeling performance, the 105B model is on par with LLMs of similar size: gpt-oss 120B and Qwen3-Next (80B…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <svg fill="none" height="16" stroke="rgb(0, 118, 255)" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewbox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="m6 17 5-5-5-5"></path><path d="m13 17 5-5-5-5"></path></svg>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><img src="https://substackcdn.com/image/fetch/%24s\_!v1hC!,w\_200,h\_200,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F273f9602-842d-4512-859c-6a47d17bbf71\_5789x5861.png" style="text-decoration: unset;list-style: none;border-radius: 8px;width: 100px;max-width: 550px;border: none;vertical-align: middle;max-height: 100px;object-fit: cover;margin: 0px"/></td></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">112</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">4</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!j45G!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">7</span>
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
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@natolambert/note/c-224489071?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"><div style="text-decoration: unset;list-style: none;padding-left: 44px;padding-bottom: 14px"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!iOMz!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D32%26fill%3D%2523808080%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="16"/></td>
<td style="min-width:8px;" width="8"></td>
<td style="vertical-align:middle;"><img height="20" src="https://substackcdn.com/image/fetch/%24s\_!VC2M!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8\_1242x1595.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 20px;height: 20px;min-width: 20px;min-height: 20px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="20"/></td>
<td style="min-width:8px;" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Cameron R. Wolfe, Ph.D. liked</div></td>
</tr></tbody></table></div></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!RihO!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F8fedcdfb-e137-4f6a-9089-a46add6c6242\_500x500.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width:12px;" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Nathan Lambert</span></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!uCNK!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">6d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Touch grass (and mud and…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <svg fill="none" height="16" stroke="rgb(0, 118, 255)" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewbox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="m6 17 5-5-5-5"></path><path d="m13 17 5-5-5-5"></path></svg>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><img src="https://substackcdn.com/image/fetch/%24s\_!yyrO!,w\_200,h\_200,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6c6328dd-0006-467c-9519-1ac6b84f25c5\_3088x2316.heic" style="text-decoration: unset;list-style: none;border-radius: 8px;width: 100px;max-width: 550px;border: none;vertical-align: middle;max-height: 100px;object-fit: cover;margin: 0px"/></td></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">75</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">2</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!j45G!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px"> </span>
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
<a data-component-name="EmailCommentEmbed" href="https://substack.com/@chocolatemilkcultleader/note/c-224572530?utm\_source=feed-email-digest" style="list-style: none;border-radius: 20px;display: block;padding: 24px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(255,255,255);width: 468px;text-decoration: none;color: rgb(54,55,55);"></a><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:top;"><img height="56" src="https://substackcdn.com/image/fetch/%24s\_!0X66!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F48081c70-8afa-41e3-a44e-b0f917bc7577\_1200x1600.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 56px;height: 56px;min-width: 56px;min-height: 56px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="56"/></td>
<td style="min-width:12px;" width="12"></td>
<td style="vertical-align:top;width:100%;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="line-height:1;width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;white-space: nowrap">Devansh</span></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;align-items: center;display: flex;"><img alt="" height="16" src="https://substackcdn.com/image/fetch/%24s\_!uCNK!,w\_32,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FBestsellerBadgeOutlineIcon%3Fv%3D4%26height%3D32%26strokeWidth%3D3.6" style="border: none;vertical-align: middle;max-width: 16px" width="16"/></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="vertical-align:middle;"><div style="text-decoration: unset;list-style: none;padding-left: 4px;padding-right: 4px;border: 1px solid rgb(0,0,0,.1);background-color: rgb(238,238,238);white-space: nowrap;border-radius: 4px"><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 11px;line-height: 16px;font-weight: 600;" translated="">You follow</div></div></td>
<td style="min-width:6px;" width="6"></td>
<td style="text-align: right;vertical-align: middle;width: 100%"><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 13px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;display: inline">6d</span></td>
</tr></tbody></table></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;color: unset;text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">MiniMax scores 80.2% on SWE-Bench at $0.30/M tokens. Claude Opus scores 80.8% at $5.00. You're paying 19x more for six-tenths of a percentage point that NIST says might be noise. But there's more. Ten frontier models launched in February. The top five cluster within 2.5 points. For pattern-matching workloads, the models are functionally interchangeable . So how do labs actually differentiate their offering and stand out against the competition? I spent a few weeks digging through the data for this month's report and three strategies stood out. Google is doing something clever that I think is underappreciated. Flash handles the cheap high-volume work, you burn through tokens, your credits accumulate, your pricing tier rises. By the time you actually need a premium model Gemini Pro is just sitting there at $2/M. The commodity model isn't the product, it's the on-ramp. Their cloud margins nearly doubled in a year so…</div></td></tr>
<tr height="4"><td></td></tr>
<tr><td><div style="list-style: none;text-decoration: unset;color: rgb(0,93,217);margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 400;">Read More <svg fill="none" height="16" stroke="rgb(0, 118, 255)" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewbox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="m6 17 5-5-5-5"></path><path d="m13 17 5-5-5-5"></path></svg>
</div></td></tr>
</tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><img src="https://substackcdn.com/image/fetch/%24s\_!6UaQ!,w\_200,h\_200,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0e53c4bc-2c79-45d0-ae23-009984711c70\_4500x2700.png" style="text-decoration: unset;list-style: none;border-radius: 8px;width: 100px;max-width: 550px;border: none;vertical-align: middle;max-height: 100px;object-fit: cover;margin: 0px"/></td></tr></tbody></table></td></tr>
<tr height="12"><td></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="width:100%;" width="100%"><tbody><tr>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!F4ic!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D28%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">18</span>
</td>
<td width="15%">
<img alt="" height="14" src="https://substackcdn.com/image/fetch/%24s\_!CRYW!,w\_28,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteReplyIcon%3Fv%3D4%26height%3D28%26stroke%3D%2523808080%26strokeWidth%3D3" style="max-width: 550px;border: none;display: inline-block;vertical-align: middle" width="14"/><span style="list-style: none;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-size: 12px;line-height: 20px;font-family: 'Jetbrains Mono',monospace;font-weight: 600;text-transform: uppercase;letter-spacing: -.2px;margin-left: 4px">2</span>
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
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!VC2M!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F69aba7df-b571-4609-aa47-fc2d031c11b8\_1242x1595.jpeg" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!mcL6!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F3403a50f-4e67-40d2-aa6f-a8d845f19c1c\_480x480.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><img height="24" src="https://substackcdn.com/image/fetch/%24s\_!aGhb!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff973d71b-ef75-4ed7-b779-c31ce2eb2d94\_1008x1008.png" style="box-sizing: border-box;max-width: 550px;border: none;vertical-align: middle;width: 24px;height: 24px;min-width: 24px;min-height: 24px;object-fit: cover;margin: 0px;display: inline;border-radius: 50%" width="24"/></td>
<td style="vertical-align:middle;"><svg fill="none" height="24" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewbox="0 0 24 24" width="24" xmlns="http://www.w3.org/2000/svg"><circle cx="12" cy="12" r="1"></circle><circle cx="19" cy="12" r="1"></circle><circle cx="5" cy="12" r="1"></circle></svg></td>
</tr></tbody></table></td>
<td style="min-width:8px;" width="8"></td>
<td style="vertical-align:middle;"><div style="list-style: none;color: rgb(255,255,255);text-decoration: unset;margin: 0;font-size: 15px;line-height: 20px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 600;" translated="">See more notes in the Substack app</div></td>
</tr></tbody></table>
</td></tr></tbody></table></td></tr>
</tbody></table></td></tr>
<tr height="16"><td></td></tr>
<tr><td><div style="color: rgb(119,119,119);text-align: center;padding: 24px0;">
<div style="padding-bottom:24px;"><p style="list-style: none;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;line-height: 16px;margin: 0;color: rgb(119,119,119);font-size: 12px;text-decoration: unset;">© 2026 <span>Substack Inc.</span><br/>548 Market Street PMB 72296, San Francisco, CA 94104 <br/><a href="https://substack.com/api/v1/email/notification/unsubscribe?token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInRvcGljIjoicmVhZGVyX3B1YmxpY2F0aW9uX3JlY29tbWVuZGF0aW9uIiwiaWF0IjoxNzczNDQ4NzEzLCJleHAiOjE4MDQ5ODQ3MTMsImlzcyI6InB1Yi0wIiwic3ViIjoibm90aWZpY2F0aW9uLXVuc3Vic2NyaWJlIn0.Ty8jOzATVnIAmrmsqGkKzRc\_BRuIcsd01t9apSGk\_dU" style="text-decoration: underline;color: rgb(119,119,119);"><span style="color: rgb(119,119,119);text-decoration: underline;">Unsubscribe</span></a></p></div>
<p style="padding: 0 24px;line-height: 20px;margin: 0;color: rgb(119,119,119);font-size: 12px;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;margin-top: 0;"><a href="https://substack.com/signup?utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=footer&amp;utm\_campaign=autofilled-footer&amp;freeSignupEmail=imeobvnk@library.readwise.io&amp;r=6q6egl" style="color: rgb(119,119,119);text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Start writing" height="40" src="https://substackcdn.com/image/fetch/%24s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!wgfj!,w\_135,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button.png, https://substackcdn.com/image/fetch/$s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!KjtY!,w\_405,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="135"/></a></p>
</div></td></tr>
<tr height="16"><td></td></tr>
<tr><td><div style="height: 1px;color: rgba(254, 254, 254, 0.01);overflow: hidden;">935</div></td></tr>
</tbody></table></td>
<td style="color:transparent;"> </td>
</tr></tbody></table>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjYwMzE0MDAzODMyLjMuZDhmMWU1MjAyOTRhOTE2OS5xbG5lMGJha0BtZy1kMS5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMS5zdWJzdGFjay5jb20iLCJwIjpudWxsLCJ0IjpudWxsLCJhIjpudWxsLCJzIjpudWxsLCJjIjoiZmVlZC1kaWdlc3QtZW1haWwiLCJmIjp0cnVlLCJwb3NpdGlvbiI6ImJvdHRvbSIsImlhdCI6MTc3MzQ0ODcxMywiZXhwIjoxNzc2MDQwNzEzLCJpc3MiOiJwdWItMCIsInN1YiI6ImVvIn0.QbBm3KaZFT4T9eG2PfPpbm5ksVr5twiY2iqPa75yaFc" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><img alt="" height="1" src="https://email.mg-d1.substack.com/o/eJxskMuK6zAYg5\_meNfgW-Jk4WcJvig5P43tju009O2HFgZmMUvpQ0gouI691JfdgHiLtKP1G5Kjg0WrFs\_nMDFYYYzSejZCsQ9cd2RU1xFX139RMUv23\_IQggEfJccYBQSwxDiZUaggNDQYWcnlxJXQnKtZyUENcd4ERsnlot0ipmX4OjK4d\_d\_mqf9FsXQTt-6C\_chlMSorVvFZ4vt9QTLpdNGwXUqee2vB2yFi6jr4\_THj18RSkrI8SNZtZRQ\_DO\_Sw7y1dXX8I5d1DBQYe30sSRH2V7XxfofJ50NdaVoNZ\_MNBq9sKeV3wEAAP\_\_qDRxRA" width="1"/>
</div>
