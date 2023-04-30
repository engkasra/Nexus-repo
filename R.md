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

### Step 2 — Connecting R to Nexus repository
change content in `Rprofile.site` or make file in `~/.Rprofile`
1. `nano /etc/R/Rprofile.site`
2. `nano ~/.Rprofile`
and add following codes:
```bash
# ## Example of .Rprofile
# options(width=65, digits=5)
# options(show.signif.stars=FALSE)
# setHook(packageEvent("grDevices", "onLoad"),
#         function(...) grDevices::ps.options(horizontal=FALSE))
# set.seed(1234)
# .First <- function() cat("\n   Welcome to R!\n\n")
# .Last <- function()  cat("\n   Goodbye!\n\n")

# ## Example of Rprofile.site
# local({
#  # add MASS to the default packages, set a CRAN mirror
#  old <- getOption("defaultPackages"); r <- getOption("repos")
#  r["CRAN"] <- "http://my.local.cran"
#  options(defaultPackages = c(old, "MASS"), repos = r)
#})

## We set the cloud mirror, which is 'network-close' to everybody, as default
local({
    r <- getOption("repos")
    r["CRAN"] <- "https://localhost/repository/<rep-name>"
    options(repos = r)
})
```
