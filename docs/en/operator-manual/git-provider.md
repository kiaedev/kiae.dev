## GitHub

### New Oauth2 Application

Register a new application with [GitHub](https://github.com/settings/applications/new) ensuring the callback URL is `(origin)/provider/oauth2/callback`. For example if your visit endpint at `https://kiae.example.com/` the callback would be `https://kiae.example.com/provider/oauth2/callback`.

### New GitHub Provider

Visit the ops admin dashboard to configure the github provider.

Input the ClientID and the ClientSecret that from the Github Oauth2 Application

![github](/assets/images/SCR-20221126-dlf.png)

## GitLab

### New Oauth2 Application

Register a new application via User Settings -> Applications ensuring the callback URL is `(origin)/provider/oauth2/callback`. For example if your visit endpint at `https://kiae.example.com/` the callback would be `https://kiae.example.com/provider/oauth2/callback`.

The application requires the user to grant the `api` scopes.

### New Gitlab Provider

Visit the ops admin dashboard to configure the gitlab provider.

Input the ClientID and the ClientSecret that from the Gitlab Application

![gitlab](/assets/images/SCR-20221126-e2n.png)
