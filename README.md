# iac_checkov
figuring out checkov 
will update as i figure more stuff out
# This is the checkov workflow with actions
 
 
on: [push]
jobs:
  checkov-job:
    runs-on: ubuntu-latest
    name: checkov-action
    steps:
      - name: Checkout repo
        uses: actions/checkout@master
      - name: wget the config file
        run:  mkdir config && wget -O config/checkov_config.yaml https://raw.githubusercontent.com/
      - name: print the
        run:  'ls -al'
      - name:  pull the docker
        run:  docker pull bridgecrew/checkov
      - name: mount the 2 volumes and run checkov
        run:  docker run --tty --volume $(pwd):/tf --workdir /tf bridgecrew/checkov --directory /tf/folder_1  --config-file /tf/config/checkov_config.yaml --external-checks-git https://github.com//iac_checkov.git//custom_checks
