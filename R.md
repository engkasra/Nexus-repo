### Step 1 — Installing R
Download the key and install it:
```bash
wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
```
Next, add the R source list to the sources.list.d directory, where APT will search for new sources:
```bash
echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list
```
The `[signed-by=/usr/share/keyrings/r-project.gpg]` portion of the file instructs apt to use the key that you downloaded to verify repository and file information for R packages.<br>
Next, update your package lists so APT will read the new R source:
```bash
sudo apt update
```
At this point, you’re ready to install R with the following command.
```bash
sudo apt install --no-install-recommends r-base
```
If prompted to confirm installation, press y to continue.<br> The --no-install-recommends arguments ensures that no extra packages are installed.<br>
Since this tutorial will explore installing an example package for every user on the system, start R as root so that the libraries will be available to all users automatically.<br> Alternatively, if you run the R command without sudo, a personal library can be set up for your user.
