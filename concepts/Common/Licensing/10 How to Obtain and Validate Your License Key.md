<iframe width="100%" height="476" src="https://www.youtube-nocookie.com/embed/grc-pIyOhcc?si=4F3q5Jjj2NX0nvNK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe><br>

### Obtain Your License Key

Log in to the [DevExpress Download Manager](https://www.devexpress.com/ClientCenter/DownloadManager/). Find your DevExtreme subscription license in the product list. Expand the product entry to access available downloads and additional information. Follow on-screen instructions to copy your key.

![DevExtreme Download Manager](/images/Common/licensing-key@2x.png)

[note] Every developer on your team must obtain and use their own key. Your DevExpress account manager should [Assign Licenses](https://www.devexpress.com/ClientCenter/LicenseManager) to developers as required.

### Manual Configuration

After you obtain the key from the DevExpress Download Manager, define that key as a constant in a separate file and use that constant in your application configuration.

Create a new file in the folder where you store your project sources. For example, your file path may look like this: `src/devextreme-license.ts`. Paste the license key you copied from the Download Manager:

    <!-- tab: devextreme-license.ts -->export const licenseKey = 'DEVELOPER_LICENSE_KEY’;

To allow each developer to use their own license key, do not store this file in your repository. Instruct Git to ignore the file that holds the key. To do this, add the file path to your project's `.gitignore` file:

    <!-- tab: .gitignore -->src/devextreme-key.ts

This action also ensures that your team does not commit the key by accident.

Specify your DevExtreme license key in [GlobalConfig](/api-reference/50%20Common/Object%20Structures/GlobalConfig '/Documentation/ApiReference/Common/Object_Structures/GlobalConfig'). This should be done in the entry point of the application:

    <!--JavaScript-->import config from 'devextreme/core/config'; 
    import { licenseKey } from './devextreme-license'; 
    
    config({ licenseKey });   

If your project includes sources via `<script>` tags (does not use bundlers), add a reference to the file that registers the license key: 

    <!--JavaScript--><script src="./dx.all.js" type="text/javascript"> </script> 
    <script src="./devextreme-license.js" type="text/javascript"></script>

    <!-- tab: devextreme-license.js --> DevExpress.config({ licenseKey: 'DEVELOPER_LICENSE_KEY' });

### Automated License Key File Creation

You may need to use your license key in multiple places (your projects and CI systems). In such cases, you can store your DevExtreme license in key in an environment variable. You can then read that variable's value and create necessary files on demand.  

The following code is an example of a script you may use in your projects. If the license key file does not exist, the script creates a new file and uses the `DEVEXTREME_KEY` environment variable to specify the key. 

    <!-- tab: add-devextreme-license.js -->const fs = require('fs') 
    const path = './src/devextreme-license.ts'; 
    const key = process.env.DEVEXTREME_KEY ?? ''; 

    if (key || !fs.existsSync(path)) { 
        fs.writeFileSync(path, `export const licenseKey = '${key}';`); 
    }

[note] If you do not specify the `DEVEXTREME_KEY` environment variable, the key will be empty.

You can call the `node add-devextreme-license` command to invoke the script manually. We recommend that you include this command in npm's `postinstall` script. In this case, every developer has an automatically created license key file after they install NPM modules.

    <!-- tab: package.json -->{ 
        "scripts": { 
            "postinstall": "node add-devextreme-license" 
        }, 
    }

Register the key within [GlobalConfig](/api-reference/50%20Common/Object%20Structures/GlobalConfig '/Documentation/ApiReference/Common/Object_Structures/GlobalConfig') and add the `devextreme-license.ts` file path to your project's `.gitignore` file. See the previous section for details.