# JAWS - Jeff's AWS Tool

##### Why?

I find using AWS's CLI tool a bit unwieldy, when quickly checking some environment variable, or changing one inside a task definition on AWS ECS. This tool aims to change that.

##### How?

Suppose you have a task definition `hello-app`, with a few environment variables:

```json
{
  "NODE_ENV": "development",
  "version": "0.9",
  "API_BASEURL": "http://api.example.com"
}
```

Your colleague tells you the base url of the API has changed to `https://api.example.com`, because your company is competent and wants to use HTTPS for everything. With JAWS, you can issue one simple command:

`jaws env -T hello-app -v API_BASEURL -s https://api.example.com`

Explanation:

`jaws`: my program

`env`: the used here, to view / update environment variables

`-T`: which task definition does the command apply to?

`-v`: I want to view / update a single variable

`-s`: update the mentioned variable with the following value

You can also supply the boolean flag `-p` to pretty-print the JSON to your console. This will not work with piping values (with `jq`, for instance).



You can also view all the environment variables using this:

`jaws env -T hello-app`



##### Help?

If you need help, first check `jaws -h` and `jaws env -h` to view "detailed" help texts. If you need additional help, please create an issue.