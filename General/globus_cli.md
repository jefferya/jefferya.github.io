# Globus CLI: How to

Inspired by what I've used in my other role on a remote server (no UI). The two parts:
* Globus cli to control Globus, initiate transfers, check status, etc.
* Globus Connect Personal acting as source endpoint for transfers

Requirements
* https://docs.globus.org/globus-connect-personal/firewall-configuration/
* Python 3.9 - 3.12

1. Globus CLI to control transfers

On remote: install Python CLI (location is relative to $HOME and can change)
```
python3 -m venv $HOME/globus-cli-virtualenv
source $HOME/globus-cli-virtualenv/bin/activate
pip install globus-cli
deactivate
```

To make life easier:
```
# Temporarily add Globus CLI to the $PATH variable to prevent typing the Python virtual environment directory
export PATH=$PATH:$HOME/globus-cli-virtualenv/bin
# Optional: add "$HOME/globus-cli-virtualenv/bin" to $PATH if you want
# $ echo 'export PATH=$PATH:$HOME/globus-cli-virtualenv/bin'>>$HOME/.bashrc
```

On remote: login to Globus  (if you don't have access to a browser on a remote server "--no-local-server")
```
globus login --no-local-server
```
The above CLI will present a URL to use on your local desktop to gain an auth code you paste into the remote CLI. Use `Globus ID` as the organization if you're using the login setup in [Globus File Transfer Instructions: Initial set up](https://docs.google.com/document/d/1aZMyiXgCcuVxKqS0HbheWx5dPcrUgPxbqn9MYWMP76s/edit?pli=1&tab=t.0)

Find the ID of the endpoint (skip this step as the env var below is populated for you)
```
globus endpoint search "Scholaris Data Transfer"
```

Create an environment variable to make the ID easier to use
```
export GLOBUS_ENDPOINT="f8a297f9-ee8f-4564-853b-8ef1634d6132"
```

To consent to the CLI usage of the Globus endpoint (if you don't have access to a browser on a remote server "--no-local-server"). Run the next "ls" command if this doesn't work to get the proper syntax to use in this step (or if `ls` works then all is ok)
```
globus session consent "urn:globus:auth:scope:transfer.api.globus.org:all[*https://auth.globus.org/scopes/${GLOBUS_ENDPOINT}/data_access]" --no-local-server
```

Directory Listing
```
globus ls ${GLOBUS_ENDPOINT}:.
```

How to transfer files, see next

2. Globus Personal Endpoint (https://docs.globus.org/globus-connect-personal/install/linux/)

Install & Setup
```
curl  --output globusconnectpersonal-latest.tgz https://downloads.globus.org/globus-connect-personal/linux/stable/globusconnectpersonal-latest.tgz
tar -zxvf globusconnectpersonal-latest.tgz 
cd globusconnectpersonal-3.2.6/
./globusconnectpersonal -setup --no-gui
```

By default, only the user's home directory is accessible by `globusconnectpersonal` as per `~/.globusonline/lta/config-paths`. Other directories can be shared as per <https://docs.globus.org/globus-connect-personal/install/linux/#config-paths>

Start the service
```
./globusconnectpersonal -start &
```

Test via the CLI - ls
```
globus ls "$(globus endpoint local-id)"
```

Test via the CLI - transfer. Transfer happens asynchronously - reference <https://docs.globus.org/cli/reference/transfer/#examples>
```
echo "delete me - test" > z.txt
# Scholaris UofA base directory (
export BASE_DIR=/scholaris_alberta/
globus transfer  "$(globus endpoint local-id)":z.txt ${GLOBUS_ENDPOINT}:${BASE_DIR}/z.txt
```

An example of recursive directory traverses and data encryption
```
export BASE_DIR=/scholaris_alberta/
globus transfer  "$(globus endpoint local-id)":test_delete_me ${GLOBUS_ENDPOINT}:${BASE_DIR}/test_delete_me --recursive --encrypt
```

The reference for the `globus transfer` describes other available options such as sync options: <https://docs.globus.org/cli/reference/transfer>


To get transfer status
```
globus task list
globus task show ${TASK_ID}
globus task event-list  ${TASK_ID}
```
Or via <https://app.globus.org/activity> as the status is updated at the grid level as opposed to the local level. You'll receive and email at your Globus account email address when the transfer is complete.

A link to the Globus File Manager positioned at the Scholaris endpoint <https://app.globus.org/file-manager?origin_id=f8a297f9-ee8f-4564-853b-8ef1634d6132&origin_path=%2Fscholaris_alberta%2F&two_pane=true>

3. How to close session
```
./globusconnectpersonal -stop
globus logout
```



References:
* https://docs.globus.org/cli/reference
* https://docs.globus.org/globus-connect-personal/firewall-configuration/
* https://docs.globus.org/globus-connect-personal/troubleshooting-guide/#troubleshooting_issues_connecting_to_the_globus_services
* https://docs.globus.org/globus-connect-personal/troubleshooting-guide/#gcp-network-troubleshooting
* https://docs.globus.org/cli/
* https://docs.globus.org/cli/quickstart/
