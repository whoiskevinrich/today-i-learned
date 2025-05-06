# Disabling Funding Messages

## Project-Specific: [1]  
- Navigate to your project's root directory. [1]  
- Create or edit the .npmrc file. [1]  
- Add the line `fund=false` to the file. [1]  

## Command-Line: [3]  

- Use the `--no-fund` flag with npm commands: `npm install --no-fund`. [3, 5]  
- Set the environment variable `NPM_CONFIG_FUND=false` before running npm commands. [3]  

## Global Settings: [4]  

- Run `npm config set fund false --location=global` to disable the message for all projects. [4]  

[1] https://benjamincrozat.com/disable-packages-are-looking-for-funding
[2] https://www.sololearn.com/en/Discuss/3203318/why-am-i-getting-npm-fund-error
[3] https://github.com/npm/cli/issues/595
[4] https://stackoverflow.com/questions/58972251/what-does-x-packages-are-looking-for-funding-mean-when-running-npm-install
[5] https://blog.jonrshar.pe/wtf-npm/dependencies/funding/
