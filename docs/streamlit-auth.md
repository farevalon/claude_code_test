### Authenticate: User authentication

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Creates an authenticator object for validating user credentials. Requires the streamlit-authenticator package.

```python
import streamlit_authenticator as stauth

authenticator = stauth.Authenticate( config['credentials'], config['cookie']['name'],
config['cookie']['key'], config['cookie']['expiry_days'], config['preauthorized'])

```

--------------------------------

### Start authentication flow with st.login

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

st.login() starts an authentication flow with an identity provider.

```python
st.login()
```

--------------------------------

### Import Streamlit in app.py

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/authentication/google.md

Initial import needed for the app.

```python
import streamlit as st
```

--------------------------------

### Run the Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/authentication/google.md

Start the app from the terminal. The app will be blank until you add code.

```bash
streamlit run app.py
```

--------------------------------

### st.login

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Starts an authentication flow with an identity provider. Use this to log in a user.

```APIDOC
## st.login

### Description
Starts an authentication flow with an identity provider.

### Method
Not applicable (Python function)

### Endpoint
Not applicable

### Parameters
None

### Response
Not applicable

### Request Example
```python
st.login()
```
```

--------------------------------

### st.login

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/user/login.md

Redirects the user to the configured authentication provider to log in. This function is part of the Streamlit user authentication API.

```APIDOC
## st.login

### Description
Redirects the user to the configured authentication provider to log in.

### Method
Function call

### Endpoint
streamlit.login

### Parameters
No parameters documented.

### Request Example
No request example provided.

### Response
No response schema documented.

### Response Example
No response example provided.
```

--------------------------------

### Configure Snowflake connection in .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/snowflake.md

Add connection parameters to the secrets file for Streamlit to use. This example uses key-pair authentication with a private_key_file instead of a password. The account identifier must be hyphen-separated in the format <my_organization>-<my_account>. The private_key_file path can be absolute or relative to the app's working directory.

```toml
[connections.snowflake]
account = "xxxxxxx-xxxxxxx"
user = "xxx"
private_key_file = "../xxx/xxx.p8"
role = "xxx"
warehouse = "xxx"
database = "xxx"
schema = "xxx"
```

--------------------------------

### Personalize apps for users with st.user and st.context

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/api-cheat-sheet.md

Authenticate users with st.login and st.logout, and access user info via st.user. Retrieve dictionaries of cookies, headers, locale, and browser data using st.context attributes.

```python
# Authenticate users
if not st.user.is_logged_in:
    st.login("my_provider")
f"Hi, {st.user.name}"
st.logout()

# Get dictionaries of cookies, headers, locale, and browser data
st.context.cookies
st.context.headers
st.context.ip_address
st.context.is_embedded
st.context.locale
st.context.theme.type
st.context.timezone
st.context.timezone_offset
st.context.url
```

--------------------------------

### Complete code: app.py

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/authentication/microsoft.md

Streamlit app that shows a login screen if the user is not logged in, and a personalized greeting with a logout button if logged in. Uses st.login and st.logout.

```python
import streamlit as st

def login_screen():
    st.header("This app is private.")
    st.subheader("Please log in.")
    st.button("Log in with Microsoft", on_click=st.login)

if not st.user.is_logged_in:
    login_screen()
else:
    st.header(f"Welcome, {st.user.name}!")
    st.button("Log out", on_click=st.logout)
```

--------------------------------

### Configure Snowflake connection in .snowflake/connections.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/snowflake.md

Add connection parameters to Snowflake's connections file for use with Streamlit. This example uses key-pair authentication as described in the previous option. If using a default connection, no change is needed in later steps; for named connections, include the name in st.connection.

```toml
[default]
account = "xxxxxxx-xxxxxxx"
user = "xxx"
private_key_file = "../xxx/xxx.p8"
role = "xxx"
warehouse = "xxx"
database = "xxx"
schema = "xxx"
```

--------------------------------

### Complete code: secrets.toml and app.py

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/authentication/google.md

Configuration file for Google OAuth credentials and the Streamlit app that shows a login screen or a personalized greeting. The secrets file must be placed in .streamlit/ and the app code in app.py.

```toml
[auth]
redirect_uri = "http://localhost:8501/oauth2callback"
cookie_secret = "xxx"
client_id = "xxx"
client_secret = "xxx"
server_metadata_url = "https://accounts.google.com/.well-known/openid-configuration"
```

```python
import streamlit as st

def login_screen():
    st.header("This app is private.")
    st.subheader("Please log in.")
    st.button("Log in with Google", on_click=st.login)

if not st.user.is_logged_in:
    login_screen()
else:
    st.header(f"Welcome, {st.user.name}!")
    st.button("Log out", on_click=st.logout)
```

--------------------------------

### Update Streamlit with Poetry

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/upgrade-version-streamlit.md

Get the latest Streamlit version with Poetry and verify the version.

```bash
poetry update streamlit
streamlit version
```

--------------------------------

### Run Streamlit app locally

Source: https://github.com/streamlit/docs/blob/main/content/get-started/fundamentals/tutorials/create-an-app.md

Start the Streamlit app from the command line. The app opens in a new browser tab.

```bash
streamlit run uber_pickups.py
```

--------------------------------

### Run a Streamlit app with streamlit run

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/_index.md

Use this command to launch your Streamlit app. Stop the server at any time with Ctrl+C in the terminal.

```bash
streamlit run your_script.py
```

--------------------------------

### Run Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/snowflake.md

Run the Streamlit app from the terminal in your working directory.

```bash
streamlit run streamlit_app.py
```

--------------------------------

### Check Streamlit version in script

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/sanity-checks.md

Use this snippet to verify the installed Streamlit version. Replace the contents of your script with these lines and run `streamlit run` on it to compare the printed version with the expected one.

```python
import streamlit as st
st.write(st.__version__)
```

--------------------------------

### Install and test Streamlit with pip

Source: https://github.com/streamlit/docs/blob/main/content/get-started/installation/_index.md

Installs Streamlit via pip and verifies the installation by launching the hello app. Run these commands in your terminal after setting up a Python environment.

```bash
pip install streamlit
streamlit hello
```

--------------------------------

### Install & Import

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/api-cheat-sheet.md

Install Streamlit, run an app, and import the library. The import convention is `import streamlit as st`.

```python
pip install streamlit

streamlit run first_app.py

# Import convention
>>> import streamlit as st
```

--------------------------------

### Run Streamlit as a Python module

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/architecture/run-your-app.md

Executing Streamlit as a module is useful for IDE configurations like PyCharm.

```bash
# Running
python -m streamlit run your_script.py
```

```bash
# is equivalent to:
streamlit run your_script.py
```

--------------------------------

### Run a Streamlit script

Source: https://github.com/streamlit/docs/blob/main/content/get-started/fundamentals/main-concepts.md

Starts a local Streamlit server and opens the app in a browser. Custom script arguments must be passed after two dashes to avoid being interpreted as Streamlit arguments.

```bash
streamlit run your_script.py [-- script args]
```

--------------------------------

### Run Streamlit app with new command

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/release-notes/2019.md

The new way to run a Streamlit app, creating a server that stays alive until Ctrl+C is pressed.

```bash
$ streamlit run your_script.py [script args]
```

--------------------------------

### Install & Import

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/api-cheat-sheet.md

Install Streamlit and import it in your script. Use the command line to run your app.

```APIDOC
```python
pip install streamlit

streamlit run first_app.py

# Import convention
>>> import streamlit as st
```
```

--------------------------------

### Upgrade Streamlit and check version

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/sanity-checks.md

Upgrade to the latest Streamlit version and print the installed version. Verify the printed version matches the one on PyPI. This can fix bugs that have already been resolved.

```bash
pip install --upgrade streamlit
streamlit version
```

--------------------------------

### Set entrypoint for Streamlit

Source: https://github.com/streamlit/docs/blob/main/content/deploy/tutorials/docker.md

Configures the container to run the Streamlit app with the specified server port and address.

```docker
ENTRYPOINT ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

--------------------------------

### Magic

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Any time Streamlit sees either a variable or literal value on its own line, it automatically writes that to your app using st.write.

```APIDOC
## Magic

### Description
Any time Streamlit sees either a variable or literal value on its own line, it automatically writes that to your app using `st.write`.

### Method
Magic

### Request Example
```python
"Hello **world**!"
my_data_frame
my_mpl_figure
```
```

--------------------------------

### Run Streamlit on another port with --server.port

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/sanity-checks.md

Run your app on a different port to bypass browser caching. Pass the `--server.port` argument to Streamlit on the command line.

```bash
streamlit run my_app.py --server.port=9876
```

--------------------------------

### Embed a public Streamlit app with iframe using ?embed=true

Source: https://github.com/streamlit/docs/blob/main/content/deploy/community-cloud/share-your-app/embed-your-app.md

Use this HTML iframe to embed a public Streamlit Community Cloud app. Add the query parameter `/?embed=true` to the `*.streamlit.app` URL. The `?embed=true` parameter removes the toolbar, top/bottom padding, and footer. Private apps are not supported for embedding.

```html
<iframe
  src="https://30days.streamlit.app?embed=true"
  style="height: 450px; width: 100%;"
></iframe>
```

--------------------------------

### Add service account key to .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/bigquery.md

Place the downloaded JSON key file content into the [gcp_service_account] section of your local secrets file. The Streamlit app reads secrets from .streamlit/secrets.toml in the app's root directory. Ensure this file is added to .gitignore and never committed to your GitHub repository.

```toml
# .streamlit/secrets.toml

[gcp_service_account]
type = "service_account"
project_id = "xxx"
private_key_id = "xxx"
private_key = "xxx"
client_email = "xxx"
client_id = "xxx"
auth_uri = "https://accounts.google.com/o/oauth2/auth"
token_uri = "https://oauth2.googleapis.com/token"
auth_provider_x509_cert_url = "https://www.googleapis.com/oauth2/v1/certs"
client_x509_cert_url = "xxx"
```

--------------------------------

### st.secrets

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Access secrets from a local TOML file.

```APIDOC
### Description
Access secrets from a local TOML file.

### Request Example
```python
key = st.secrets["OpenAI_key"]
```
```

--------------------------------

### Streamlit app to read CSV from S3 using FilesConnection

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/aws-s3.md

Copy this code to your Streamlit app and run it. Adapt the bucket name and file path. Streamlit automatically turns access keys from secrets into environment variables, which s3fs searches for by default. The read() method caches results for 600 seconds (ttl=600).

```python
# streamlit_app.py

import streamlit as st
from st_files_connection import FilesConnection

# Create connection object and retrieve file contents.
# Specify input format is a csv and to cache the result for 600 seconds.
conn = st.connection('s3', type=FilesConnection)
df = conn.read("testbucket-jrieke/myfile.csv", input_format="csv", ttl=600)

# Print results.
for row in df.itertuples():
    st.write(f"{row.Owner} has a :{row.Pet}:")
```

--------------------------------

### Auth0 configuration with client_kwargs prompt=login

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/authentication.md

Use this TOML configuration to force users to log in every time with Auth0 by setting prompt to "login" in client_kwargs. Streamlit defaults to scope="openid profile email" and prompt="select_account"; state and nonce are handled automatically.

```toml
[auth]
redirect_uri = "http://localhost:8501/oauth2callback"
cookie_secret = "xxx"

[auth.auth0]
client_id = "xxx"
client_secret = "xxx"
server_metadata_url = "https://{account}.{region}.auth0.com/.well-known/openid-configuration"
client_kwargs = { "prompt" = "login" }
```

--------------------------------

### Add MongoDB credentials to .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/mongodb.md

Create a .streamlit/secrets.toml file in your app's root directory with the [mongo] section containing host, port, username, and password. Replace these values with your remote database credentials when copying to Streamlit Community Cloud. Add this file to .gitignore and do not commit it to GitHub.

```toml
# .streamlit/secrets.toml

[mongo]
host = "localhost"
port = 27017
username = "xxx"
password = "xxx"
```

--------------------------------

### Define login screen function

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/authentication/microsoft.md

Displays a header, subheader, and a login button that triggers st.login as a callback. The button uses Streamlit's login command.

```python
def login_screen():
    st.header("This app is private.")
    st.subheader("Please log in.")
    st.button("Log in with Microsoft", on_click=st.login)
```

--------------------------------

### Check if Streamlit is running on remote server

Source: https://github.com/streamlit/docs/blob/main/content/kb/deployments/remote-start.md

Run this command on a Linux server via SSH to verify Streamlit is running. If the process appears, the issue is likely port exposure.

```bash
ps -Al | grep streamlit
```

--------------------------------

### AppTest.from_file

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Initializes a simulated app from a file. Use this to load a Streamlit app script from a file path for testing.

```APIDOC
## AppTest.from_file

### Description
Initializes a simulated app from a file. Use this to load a Streamlit app script from a file path for testing.

### Example
```python
from streamlit.testing.v1 import AppTest

at = AppTest.from_file("streamlit_app.py")
at.run()
```
```

--------------------------------

### st.testing.v1.AppTest: Simulate a running Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Use `st.testing.v1.AppTest` to simulate a running Streamlit app for testing. The example sets a secret, runs the app, asserts no exception, interacts with a text input, and checks a warning message.

```python
from streamlit.testing.v1 import AppTest

at = AppTest.from_file("streamlit_app.py")
at.secrets["WORD"] = "Foobar"
at.run()
assert not at.exception

at.text_input("word").input("Bazbat").run()
assert at.warning[0].value == "Try again."
```

--------------------------------

### Login with multiple OIDC providers using callbacks

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/authentication.md

Alternative Streamlit app code using on_click callbacks for login buttons. Provides the same functionality as the previous example but with callback-based event handling.

```python
import streamlit as st

if not st.user.is_logged_in:
    st.button("Log in with Google", on_click=st.login, args=["google"])
    st.button("Log in with Microsoft", on_click=st.login, args=["microsoft"])
    st.stop()

st.button("Log out", on_click=st.logout)
st.markdown(f"Welcome! {st.user.name}")
```

--------------------------------

### streamlit_app.py - dynamic role-based navigation

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/multipage-apps/dynamic-navigation.md

The entrypoint file that handles user authentication and builds a dynamic navigation menu based on the selected role. It uses st.navigation and st.Page to conditionally show pages for Requester, Responder, and Admin roles.

```python
import streamlit as st

if "role" not in st.session_state:
    st.session_state.role = None

ROLES = [None, "Requester", "Responder", "Admin"]


def login():

    st.header("Log in")
    role = st.selectbox("Choose your role", ROLES)

    if st.button("Log in"):
        st.session_state.role = role
        st.rerun()


def logout():
    st.session_state.role = None
    st.rerun()


role = st.session_state.role

logout_page = st.Page(logout, title="Log out", icon=":material/logout:")
settings = st.Page("settings.py", title="Settings", icon=":material/settings:")
request_1 = st.Page(
    "request/request_1.py",
    title="Request 1",
    icon=":material/help:",
    default=(role == "Requester"),
)
request_2 = st.Page(
    "request/request_2.py", title="Request 2", icon=":material/bug_report:"
)
respond_1 = st.Page(
    "respond/respond_1.py",
    title="Respond 1",
    icon=":material/healing:",
    default=(role == "Responder"),
)
respond_2 = st.Page(
    "respond/respond_2.py", title="Respond 2", icon=":material/handyman:"
)
admin_1 = st.Page(
    "admin/admin_1.py",
    title="Admin 1",
    icon=":material/person_add:",
    default=(role == "Admin"),
)
admin_2 = st.Page("admin/admin_2.py", title="Admin 2", icon=":material/security:")

account_pages = [logout_page, settings]
request_pages = [request_1, request_2]
respond_pages = [respond_1, respond_2]
admin_pages = [admin_1, admin_2]

st.title("Request manager")
st.logo("images/horizontal_blue.png", icon_image="images/icon_blue.png")

page_dict = {}
if st.session_state.role in ["Requester", "Admin"]:
    page_dict["Request"] = request_pages
if st.session_state.role in ["Responder", "Admin"]:
    page_dict["Respond"] = respond_pages
if st.session_state.role == "Admin":
    page_dict["Admin"] = admin_pages

if len(page_dict) > 0:
    pg = st.navigation({"Account": account_pages} | page_dict)
else:
    pg = st.navigation([st.Page(login)])

pg.run()
```

--------------------------------

### Check if Streamlit is running (ps -Al | grep streamlit)

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/sanity-checks.md

Run this command on a Mac or Linux terminal to see if the Streamlit server is running. If the output does not contain 'streamlit run' (or 'streamlit hello' if that was the command), the server is not running and you should re-run your command.

```bash
ps -Al | grep streamlit
```

--------------------------------

### Add GCS access key to .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/gcs.md

Create a `.streamlit/secrets.toml` file in your app's root directory and add the service account key under `[connections.gcs]`. Replace the placeholder values (`xxx`) with your actual credentials. Add this file to `.gitignore` and do not commit it to your GitHub repo.

```toml
# .streamlit/secrets.toml

[connections.gcs]
type = "service_account"
project_id = "xxx"
private_key_id = "xxx"
private_key = "xxx"
client_email = "xxx"
client_id = "xxx"
auth_uri = "https://accounts.google.com/o/oauth2/auth"
token_uri = "https://oauth2.googleapis.com/token"
auth_provider_x509_cert_url = "https://www.googleapis.com/oauth2/v1/certs"
client_x509_cert_url = "xxx"
```

--------------------------------

### Open Streamlit docs in browser

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/docs.md

Runs streamlit docs without a command to open the Streamlit documentation in your default browser.

```bash
streamlit docs
```

--------------------------------

### Configure AWS credentials in .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/aws-s3.md

Create a .streamlit/secrets.toml file in your app's root or home directory with your AWS access key ID, secret access key, and default region. Replace the 'xxx' placeholders with your actual values and add this file to .gitignore to avoid committing it to your repository.

```toml
# .streamlit/secrets.toml
AWS_ACCESS_KEY_ID = "xxx"
AWS_SECRET_ACCESS_KEY = "xxx"
AWS_DEFAULT_REGION = "xxx"
```

--------------------------------

### streamlit.tabs

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/layout/tabs.md

Inserts a set of tabs into the app, each containing a container for content.

```APIDOC
## streamlit.tabs

### Description
Inserts a set of tabs into the app, each containing a container for content.

### Method
`streamlit.tabs(tab_labels)`

### Parameters
- **tab_labels** (list[str]) - Required - A list of tab labels as strings.

### Returns
- **list[TabContainer]** - A list of TabContainer objects, one for each tab.

### Example
```python
import streamlit as st

tab1, tab2 = st.tabs(["Tab 1", "Tab 2"])

with tab1:
    st.write("Content of Tab 1")

with tab2:
    st.write("Content of Tab 2")
```
```

--------------------------------

### st.testing.v1.AppTest

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Simulates a running Streamlit app for testing. Use it to load an app, set secrets, run the app, and interact with elements.

```APIDOC
## st.testing.v1.AppTest

### Description
Simulates a running Streamlit app for testing. Use it to load an app, set secrets, run the app, and interact with elements.

### Example
```python
from streamlit.testing.v1 import AppTest

at = AppTest.from_file("streamlit_app.py")
at.secrets["WORD"] = "Foobar"
at.run()
assert not at.exception

at.text_input("word").input("Bazbat").run()
assert at.warning[0].value == "Try again."
```
```

--------------------------------

### AppTest.from_function

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Initializes a simulated app from a function. Use this to load a Streamlit app script from a callable function for testing.

```APIDOC
## AppTest.from_function

### Description
Initializes a simulated app from a function. Use this to load a Streamlit app script from a callable function for testing.

### Example
```python
from streamlit.testing.v1 import AppTest

at = AppTest.from_function(app_script_as_callable)
at.run()
```
```

--------------------------------

### Run multipage app with streamlit run

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/multipage-apps/page_directory.md

Run a multipage app exactly like a single-page app by passing the entrypoint file to `streamlit run`.

```bash
streamlit run your_homepage.py
```

--------------------------------

### Add Streamlit badge to GitHub README

Source: https://github.com/streamlit/docs/blob/main/content/deploy/community-cloud/share-your-app/_index.md

Markdown snippet to embed the Streamlit badge in your GitHub README.md. Replace the placeholder URL with your deployed app's URL.

```markdown
[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://<your-custom-subdomain>.streamlit.app)
```

--------------------------------

### Upgrade Streamlit with pip

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/release-notes/_index.md

Run this command to upgrade to the latest version of Streamlit.

```bash
pip install --upgrade streamlit
```

--------------------------------

### Run Streamlit app the old way (no app produced)

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/release-notes/2019.md

Running the script directly with Python executes it but does not produce a Streamlit app.

```bash
$ python your_script.py
```

--------------------------------

### $ streamlit version

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/version.md

Prints the Streamlit version number. This command is equivalent to executing `streamlit --version`.

```APIDOC
## `$ streamlit version`

### Description
Print Streamlit's version number. This command is equivalent to executing `streamlit --version`.

### Syntax
```
streamlit version
```
```

--------------------------------

### secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Save your secrets in a per-project or per-profile TOML file.

```APIDOC
### Description
Save your secrets in a per-project or per-profile TOML file.

### Request Example
```python
OpenAI_key = "<YOUR_SECRET_KEY>"
```
```

--------------------------------

### Install Streamlit agent skills

Source: https://github.com/streamlit/docs/blob/main/content/get-started/installation/command-line.md

Installs Streamlit's official agent skills for AI coding agents so they follow current Streamlit APIs.

```bash
streamlit skills
```

--------------------------------

### st.logout

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Removes a user's identity information. Use this to log out a user.

```APIDOC
## st.logout

### Description
Removes a user's identity information.

### Method
Not applicable (Python function)

### Endpoint
Not applicable

### Parameters
None

### Response
Not applicable

### Request Example
```python
st.logout()
```
```

--------------------------------

### Print Streamlit version

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/version.md

Use this command to display the installed Streamlit version. It is equivalent to `streamlit --version`.

```bash
streamlit version
```

--------------------------------

### Add MySQL credentials to .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/mysql.md

TOML configuration for st.connection to MySQL. Requires streamlit>=1.35.0 if 'query' is used. Replace placeholder values with actual database credentials.

```toml
# .streamlit/secrets.toml

[connections.mysql]
dialect = "mysql"
host = "localhost"
port = 3306
database = "xxx"
username = "xxx"
password = "xxx"
query = { charset = "xxx" }
```

--------------------------------

### streamlit help command

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/help.md

Prints the available commands for the Streamlit CLI tool. Equivalent to executing `streamlit --help`.

```bash
streamlit help
```

--------------------------------

### st.logout()

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/authentication.md

Clears `st.user` and removes the identity cookie from the user's browser. If your identity provider supports it, Streamlit then redirects the user to your identity provider to log out there, too. Finally, Streamlit redirects the user to the homepage of your app in a new session.

```APIDOC
## st.logout()

### Description
Clears `st.user` and removes the identity cookie from the user's browser. If your identity provider supports it, Streamlit then redirects the user to your identity provider to log out there, too. Finally, Streamlit redirects the user to the homepage of your app in a new session.

### Method
N/A (Streamlit command)

### Endpoint
N/A (Streamlit command)

### Parameters
None

### Response
No return value.
```

--------------------------------

### st.connections.BaseConnection

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Build your own connection with `BaseConnection`.

```APIDOC
### Description
Build your own connection with `BaseConnection`.

### Request Example
```python
class MyConnection(BaseConnection[myconn.MyConnection]):
    def _connect(self, **kwargs) -> MyConnection:
        return myconn.connect(**self._secrets, **kwargs)
    def query(self, query):
        return self._instance.query(query)
```
```

--------------------------------

### Log out a user with st.logout

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

st.logout() removes a user's identity information.

```python
st.logout()
```

--------------------------------

### streamlit run syntax

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/run.md

Shows the general syntax for the streamlit run command. The entrypoint file or directory is optional; if omitted, Streamlit tries to run streamlit_app.py from the current working directory.

```bash
streamlit run [<entrypoint file or directory>] [-- config options] [script args]
```

--------------------------------

### Install Streamlit with pip

Source: https://github.com/streamlit/docs/blob/main/content/get-started/installation/command-line.md

Installs Streamlit into the activated virtual environment using pip.

```bash
pip install streamlit
```

--------------------------------

### st.components.v1.iframe

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Load a remote URL in an iframe. Deprecated in version 1.56.0. Use `st.iframe` instead.

```APIDOC
## st.components.v1.iframe

### Description
Load a remote URL in an iframe.

### Method
N/A (Python function)

### Endpoint
N/A

### Parameters
- `url` (string) - Required - The URL to load.

### Response
N/A

### Request Example
```python
from streamlit.components.v1 import iframe
iframe(
    "https://docs.streamlit.io"
)
```
```

--------------------------------

### Configure SSL certificate and key in .streamlit/config.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/configuration/https.md

Set server.sslCertFile and server.sslKeyFile to local file paths for the certificate chain and private key. Both must be specified or the app will exit with an error. This option is not recommended for production; use a reverse proxy or load balancer instead.

```toml
# .streamlit/config.toml

[server]
sslCertFile = '/path/to/certchain.pem'
sslKeyFile = '/path/to/private.key'
```

--------------------------------

### Downgrade Streamlit with pip install

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/sanity-checks.md

Downgrade Streamlit to a specific version using pip. Replace `1.0.0` with the desired version.

```bash
pip install --upgrade streamlit==1.0.0
```

--------------------------------

### Install streamlit-nightly package

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/prerelease-features.md

Uninstall the standard streamlit package and install the nightly build. Never have both installed in the same environment.

```bash
pip uninstall streamlit
pip install streamlit-nightly --upgrade
```

--------------------------------

### st.user

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Returns information about a logged-in user. Use this to access user details.

```APIDOC
## st.user

### Description
Returns information about a logged-in user.

### Method
Not applicable (Python attribute)

### Endpoint
Not applicable

### Parameters
None

### Response
- `is_logged_in` (boolean) - Whether the user is logged in.
- `name` (string) - The user's name.

### Request Example
```python
if st.user.is_logged_in:
  st.write(f"Welcome back, {st.user.name}!")
```
```

--------------------------------

### Run Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/get-started/installation/command-line.md

Runs your Streamlit app. If the short command fails, use the long-form command.

```bash
streamlit run app.py
```

```bash
python -m streamlit run app.py
```

--------------------------------

### Use SQL connection in Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/connecting-to-data.md

Create a SQL connection to `pets_db`, insert data using `conn.session`, and query it back with `conn.query()`. Without a `ttl=` value, Streamlit caches the query result indefinitely.

```python
# streamlit_app.py

import streamlit as st
from sqlalchemy import text

# Create the SQL connection to pets_db as specified in your secrets file.
conn = st.connection('pets_db', type='sql')

# Insert some data with conn.session.
with conn.session as s:
    s.execute(text('CREATE TABLE IF NOT EXISTS pet_owners (person TEXT, pet TEXT);'))
    s.execute(text('DELETE FROM pet_owners;'))
    pet_owners = {'jerry': 'fish', 'barbara': 'cat', 'alex': 'puppy'}
    for k in pet_owners:
        s.execute(
            text('INSERT INTO pet_owners (person, pet) VALUES (:owner, :pet);'),
            params=dict(owner=k, pet=pet_owners[k])
        )
    s.commit()

# Query and display the data you inserted
pet_owners = conn.query('select * from pet_owners')
st.dataframe(pet_owners)
```

--------------------------------

### Streamlit version requirement

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/execution-flow/fragments/start-and-stop-fragment-auto-reruns.md

Specifies the minimum required Streamlit version for this tutorial. Install or upgrade Streamlit to at least this version to use the features demonstrated.

```text
streamlit>=1.37.0
```

--------------------------------

### FrontendRendererArgs

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Type alias for the component arguments.

```APIDOC
## FrontendRendererArgs

### Description
Type alias for the component arguments.

### Method
N/A (Type alias)

### Endpoint
N/A

### Parameters
N/A

### Response
N/A

### Request Example
```typescript
import { FrontendRendererArgs } from "@streamlit/component-v2-lib";
```
```

--------------------------------

### streamlit docs syntax

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/docs.md

Shows the command syntax for the streamlit docs CLI. The <command> argument is optional; if omitted, Streamlit opens the docs in the default browser, otherwise it prints the signature and docstring of the specified command.

```bash
streamlit docs <command>
```

--------------------------------

### Snowflake account identifier

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/snowflake.md

Account identifier in hyphen-separated format required by the Snowflake Connector for Python. Copy from Snowflake and change the period to a hyphen.

```toml
account = "xxxxxxx-xxxxxxx"
```

--------------------------------

### Example script with imports

Source: https://github.com/streamlit/docs/blob/main/content/deploy/concepts/dependencies.md

A simple Streamlit script that imports streamlit, pandas, numpy, math, and random. Only streamlit needs to be installed because pandas and numpy are direct dependencies of streamlit, and math and random are built into Python.

```python
import streamlit as st
import pandas as pd
import numpy as np
import math
import random

st.write('Hi!')
```

--------------------------------

### Configure secrets.toml for ClickHouse Managed Postgres

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/clickhouse-managed-postgres.md

Create .streamlit/secrets.toml with connection details for ClickHouse Managed Postgres. Replace host and credentials with your instance's direct connection details. sslmode = "verify-full" checks the server certificate and hostname; sslrootcert is resolved from the working directory, so run Streamlit from the directory containing ca-certificate.pem.

```toml
# .streamlit/secrets.toml

[connections.clickhouse_managed_postgres]
dialect = "postgresql"
driver = "psycopg2"
host = "YOUR_HOST.pg.clickhouse.cloud"
port = 5432
database = "postgres"
username = "postgres"
password = "YOUR_PASSWORD"

[connections.clickhouse_managed_postgres.create_engine_kwargs.connect_args]
sslmode = "verify-full"
sslrootcert = "ca-certificate.pem"
```

--------------------------------

### Simple Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/deploy/community-cloud/get-started/security-model.md

This Python code demonstrates a minimal Streamlit app with a slider and text output. Used to illustrate the basic structure of a Streamlit application.

```python
import streamlit as st
number = st.slider("Pick a number: ", min_value=1, max_value=10)
st.text("Your number is " + str(number))

```

--------------------------------

### Add OpenAI API key to Streamlit secrets

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/llms/conversational-apps.md

Create a `.streamlit/secrets.toml` file in the project directory and add the OpenAI API key. Replace `YOUR_API_KEY` with your actual key.

```toml
# .streamlit/secrets.toml
OPENAI_API_KEY = "YOUR_API_KEY"
```

--------------------------------

### Add Supabase URL and API key to .streamlit/secrets.toml

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/supabase.md

TOML configuration for storing Supabase credentials in Streamlit secrets. Replace 'xxxx' with your Project URL and API key. Ensure this file is added to .gitignore.

```toml
# .streamlit/secrets.toml

[connections.supabase]
SUPABASE_URL = "xxxx"
SUPABASE_KEY = "xxxx"
```

--------------------------------

### Create project files in current working directory

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/init.md

Run `streamlit init` in the current working directory. Streamlit creates `requirements.txt` and `streamlit_app.py` in the CWD. After creation, Streamlit prompts `❓ Run the app now? [Y/n]`; entering `Y` is equivalent to running `streamlit run streamlit_app.py`.

```bash
streamlit init
```

```text
CWD/
├── requirements.txt
└── streamlit_app.py
```

--------------------------------

### Local app secrets for PostgreSQL connection

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/postgresql.md

TOML configuration for .streamlit/secrets.toml defining the PostgreSQL connection parameters (dialect, host, port, database, username, password). Replace the placeholder values with your actual database credentials. Keep this file out of version control.

```toml
# .streamlit/secrets.toml

[connections.postgresql]
dialect = "postgresql"
host = "localhost"
port = "5432"
database = "xxx"
username = "xxx"
password = "xxx"
```

--------------------------------

### Create requirements.txt with Streamlit and ClickHouse Connect dependencies

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/clickhouse.md

Lists the required Python packages: streamlit, clickhouse-connect with SQLAlchemy support, and sqlalchemy. Install with pip.

```txt
streamlit>=1.28
clickhouse-connect[sqlalchemy]
sqlalchemy>=2.0.0
```

--------------------------------

### FrontendState

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Type alias for the component state.

```APIDOC
## FrontendState

### Description
Type alias for the component state.

### Method
N/A (Type alias)

### Endpoint
N/A

### Parameters
N/A

### Response
N/A

### Request Example
```typescript
import { FrontendState } from "@streamlit/component-v2-lib";
```
```

--------------------------------

### Run Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/tutorials/databases/clickhouse-managed-postgres.md

Run the app with streamlit run streamlit_app.py. The app displays a screenshot of the finished app with the sample data.

```bash
streamlit run streamlit_app.py
```

--------------------------------

### Show all configuration options with streamlit config show

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/configuration/config-toml.md

Run this command in your terminal or CLI to display all available configuration options for your Streamlit app.

```bash
streamlit config show
```

--------------------------------

### Login with multiple OIDC providers using st.login

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/authentication.md

Streamlit app code that provides separate login buttons for Google and Microsoft using the st.login method. After login, displays a logout button and a welcome message with the user's name.

```python
import streamlit as st

if not st.user.is_logged_in:
    if st.button("Log in with Google"):
        st.login("google")
    if st.button("Log in with Microsoft"):
        st.login("microsoft")
    st.stop()

if st.button("Log out"):
    st.logout()
st.markdown(f"Welcome! {st.user.name}")
```

--------------------------------

### streamlit cache clear

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/cache.md

Clears persisted files from the on-disk Streamlit cache. This command is used to remove cached data that has been stored on disk by Streamlit's caching mechanisms.

```APIDOC
## streamlit cache clear

### Description
Clear persisted files from the on-disk Streamlit cache, if present.

### Method
CLI Command

### Command
`streamlit cache clear`

### Syntax
```
streamlit cache clear
```

### Parameters
None

### Response
No response body. The command exits with a success status if the cache was cleared successfully.

```

--------------------------------

### st.context

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

`st.context` provides a read-only interface to access cookies, headers, locale, and other browser-session information.

```APIDOC
### Description
`st.context` provides a read-only interface to access cookies, headers, locale, and other browser-session information.

### Request Example
```python
st.context.cookies
st.context.headers
```
```

--------------------------------

### Create project files in another directory

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/init.md

Run `streamlit init project` to create a new project in the `project` subdirectory. Streamlit creates `requirements.txt` and `streamlit_app.py` inside `project/`. After creation, Streamlit prompts `❓ Run the app now? [Y/n]`; entering `Y` is equivalent to running `streamlit run project/streamlit_app.py`.

```bash
streamlit init project
```

```text
CWD/
└── project/
    ├── requirements.txt
    └── streamlit_app.py
```

--------------------------------

### Start Streamlit on port 80

Source: https://github.com/streamlit/docs/blob/main/content/kb/deployments/remote-start.md

Use the --server.port option to expose Streamlit on port 80, which some hosts open by default.

```bash
streamlit run my_app.py --server.port=80
```

--------------------------------

### Access secrets in a Streamlit app

Source: https://github.com/streamlit/docs/blob/main/content/develop/concepts/connections/secrets-management.md

Shows how to access secrets via st.secrets dict and as environment variables. Root-level secrets are available as environment variables; section contents are not.

```python
import streamlit as st

# Everything is accessible via the st.secrets dict:

st.write("DB username:", st.secrets["db_username"])
st.write("DB password:", st.secrets["db_password"])

# And the root-level secrets are also accessible as environment variables:

import os

st.write(
    "Has environment variables been set:",
    os.environ["db_username"] == st.secrets["db_username"],
)
```

--------------------------------

### Update Streamlit with conda (Conda)

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/upgrade-version-streamlit.md

Step 2 of the Conda upgrade workflow: update Streamlit within the active conda environment and verify the version.

```bash
conda update -c conda-forge streamlit -y
streamlit version
```

--------------------------------

### Activate environment and upgrade Streamlit (Pipenv)

Source: https://github.com/streamlit/docs/blob/main/content/kb/FAQ/upgrade-version-streamlit.md

Step 2 of the Pipenv upgrade workflow: activate the environment, upgrade Streamlit with pip, and verify the version.

```bash
pipenv shell
pip install --upgrade streamlit
streamlit version
```

--------------------------------

### Import FrontendState type

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Imports the FrontendState type alias from @streamlit/component-v2-lib.

```typescript
import { FrontendState } from "@streamlit/component-v2-lib";
```

--------------------------------

### Light theme embed option

Source: https://github.com/streamlit/docs/blob/main/content/deploy/community-cloud/share-your-app/embed-your-app.md

Opens the embedded app with light theme.

```javascript
/?embed=true&embed_options=light_theme
```

--------------------------------

### Downgrade Streamlit with conda

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/release-notes/2019.md

Command to downgrade Streamlit to version 0.37 using conda.

```bash
conda install streamlit=0.37
```

--------------------------------

### FrontendRenderer

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Type alias for the component function.

```APIDOC
## FrontendRenderer

### Description
Type alias for the component function.

### Method
N/A (Type alias)

### Endpoint
N/A

### Parameters
N/A

### Response
N/A

### Request Example
```typescript
import { FrontendRenderer } from "@streamlit/component-v2-lib";
```
```

--------------------------------

### Downgrade Streamlit with pip

Source: https://github.com/streamlit/docs/blob/main/content/develop/quick-references/release-notes/2019.md

Command to downgrade Streamlit to version 0.37 using pip.

```bash
pip install --upgrade streamlit==0.37
```

--------------------------------

### Launch Streamlit Hello example app

Source: https://github.com/streamlit/docs/blob/main/content/get-started/installation/command-line.md

Tests the installation by launching the Streamlit Hello example app. If the short command fails, use the long-form command.

```bash
streamlit hello
```

```bash
python -m streamlit hello
```

--------------------------------

### Install Streamlit AI coding skills

Source: https://github.com/streamlit/docs/blob/main/content/get-started/fundamentals/additional-features.md

Run this command in your project to install official Streamlit skills for AI coding agents. Use `streamlit skills --global` to install them once for every project on your machine.

```bash
streamlit skills
```

--------------------------------

### st.connection

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/connections/connection.md

Creates a connection to a data source or API for accessing external data in your Streamlit app. This is the main API for establishing connections to databases, APIs, and other external data sources.

```APIDOC
## st.connection

### Description
Creates a connection to a data source or API for accessing external data in your Streamlit app.

### Method
st.connection

### Signature
streamlit.connection(name, type=None, **kwargs)

### Parameters
- **name** (str) - Required - The name of the connection.
- **type** (str or type) - Optional - The type of connection to create.
- **kwargs** - Optional - Additional keyword arguments to pass to the connection.

### Returns
A connection object that can be used to query the data source.

### Notes
- This function was previously known as `st.experimental_connection`.
- For a deeper dive into creating and managing data connections, see the [Connecting to data](/develop/concepts/connections/connecting-to-data) documentation.
```

--------------------------------

### Show footer embed option

Source: https://github.com/streamlit/docs/blob/main/content/deploy/community-cloud/share-your-app/embed-your-app.md

Shows the footer reading "Made with Streamlit." Note: This does not apply to Streamlit versions 1.29.0 and later since the footer was removed from the library.

```javascript
/?embed=true&embed_options=show_footer
```

--------------------------------

### st_cropper from streamlit-cropper

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

A simple image cropper for Streamlit. Created by @turner-anderson.

```python
from streamlit_cropper import st_cropper

st_cropper(img, realtime_update=realtime_update, box_color=box_color, aspect_ratio=aspect_ratio)
```

--------------------------------

### Access context with st.context

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/_index.md

Read-only interface to access cookies, headers, locale, and other browser-session information. Example shows accessing cookies and headers.

```python
st.context.cookies
st.context.headers
```

--------------------------------

### Example requirements.txt

Source: https://github.com/streamlit/docs/blob/main/content/deploy/tutorials/docker.md

Lists Python dependencies for the Streamlit app, including altair, pandas, and streamlit.

```text
altair
pandas
streamlit
```

--------------------------------

### streamlit init

Source: https://github.com/streamlit/docs/blob/main/content/develop/api-reference/command-line/init.md

Documentation for the streamlit init command, including syntax, arguments, and usage examples.

```APIDOC
## streamlit init

### Description
Creates the files for a new Streamlit app project, including `requirements.txt` and `streamlit_app.py`.

### Syntax
```
streamlit init <directory>
```

### Arguments
- `<directory>` (Optional): The directory location of the new project. If no directory is provided, the current working directory will be used.

### Examples

#### Example 1: Create project files in the current working directory

1. Execute the following command:
   ```bash
   streamlit init
   ```
   Streamlit creates the following files:
   ```
   CWD/
   ├── requirements.txt
   └── streamlit_app.py
   ```
2. Streamlit prompts: `❓ Run the app now? [Y/n]`. Enter `Y` for yes. This is equivalent to executing `streamlit run streamlit_app.py` from your current working directory.
3. Begin editing your `streamlit_app.py` file and save your changes.

#### Example 2: Create project files in another directory

1. Execute the following command:
   ```bash
   streamlit init project
   ```
   Streamlit creates the following files:
   ```
   CWD/
   └── project/
       ├── requirements.txt
       └── streamlit_app.py
   ```
2. Streamlit prompts: `❓ Run the app now? [Y/n]`. Enter `Y` for yes. This is equivalent to executing `streamlit run project/streamlit_app.py` from your current working directory.
3. Begin editing your `streamlit_app.py` file and save your changes.
```