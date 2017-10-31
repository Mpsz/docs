Log in to AWS, and navigate to [CloudFront](https://console.aws.amazon.com/cloudfront).

![](/cloudfront.png)

Click **Create Distribution**.

You can choose the delivery method for your content. Click **Get Started** under the **Web** section.

![](/delivery-method.png)

Next, configure your distribution settings. 

Under **Origin Settings**, here are the values you'll need to change:

| Parameter | Value |
| - | - |
| Origin Domain Name | Set to `custom-domain-id.edge.tenants.auth0-region.auth0.com`. Be sure to replace the `custom-domain-id` and `auth0-region` placeholder values |
| Origin ID | A description for the origin. This value lets you distinguish between multiple origins in the same distribution and therefore must be unique. |
| Origin Protocol Policy | Set to **HTTPS Only** |

![](/create-distribution.png)

You'll also need to provide information on the **Origin Custom Headers** (the **Header Name** and **Value** fields appear only after you've provided an **Origin Domain Name**):

| Parameter | Value |
| - | - |
| Header Name | Set to `cname-api-key` |
| Value | Set to the CNAME API Key value that you were given immediately after you verified ownership of your domain name with Auth0 |

![](/origin-custom-headers.png)

Next, you'll configure the **Default Cache Behavior Settings**. Here are the values you'll need to change:

| Parameter | Value |
| - | - |
| Viewer Protocol Policy | Select **Redirect HTTP to HTTPS** |
| Allowed HTTP Methods | Select **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE** |
| Cache Based on Selected Request Headers | Select **Whitelist** |
| Whitelist Headers | Enter `User-Agent` and click **Add Custom >>** to add the custom whitelist header |
| Forward Cookies | Select **All** |
| Query String Forwarding and Caching | Select **Forward all, cache based on all** |

Scroll to the bottom of the page and click **Create Distribution**.

You'll see your newly-created distribution in your CloudFront home page.

![](/distributions.png)

Your CloudFront setup is now ready for use!