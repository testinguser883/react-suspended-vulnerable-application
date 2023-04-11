# React Suspended

A React application riddled with security vulnerabilities so you can learn how not to write insecure code.

## How to run me?

### Local installation

For a local installation, make sure you have the following dependencies installed:
1. Node.js v14 (other versions don't work)
2. npm

### Docker installation

Easiest method is to run the React app through a containerized image.
The `docker-compose.yml` file also mounts the `./src` directory to the container so you can easily edit source files on the host, and enjoy the fast development experience of hot reloading.

To run the containerized version, run the following command:


```sh
docker-compose up --build
```

Note: passing the `--build` will allow it to re-build the container image if anything changed that would require a new Docker image too.

### Reflecting changes to the development environment

If you've made significant changes that require re-building the container image, such as by adding a new dependency, you can run the following command:

```sh
docker-compose up --build
```

## How to use me?

### Attribute Cross-site Scripting (XSS)

1. Change the `src/database.json` to one of:
   1. `javascript:alert(1)`
   2. `JAVAscript:alert(1)`
   3. `\x19JAVAscript:alert(1)`

2. Use the `PackageParser` component but supply it a string instead of a JSON object:
   1. It uses `react-json-pretty` vulnerable package version
   2. Set `src/database.json` to `<img src=x on Error=alert(1) />`

---

Modern frontend frameworks like React are well thought of in their application security design and that’s great. However, there is still plenty of room for developers to make mistakes and use insecure APIs, vulnerable components, or generally do the wrong thing that turns user input into a Cross-site Scripting vulnerability (XSS). Let me show you how React applications get hacked in the real world with React Suspended educational experience.

# License

- Copyright 2020 Creative Tim (https://www.creative-tim.com/?ref=blkdsr-readme)
- Copyright 2021 Liran Tal (liran.tal@gmail.com)
- Licensed under MIT (https://github.com/creativetimofficial/blk-design-system-react/blob/main/LICENSE.md)

## Derivative work

This codebase makes use of derivative work created by [Creative Tim](https://www.creative-tim.com), in particular their open source website design # [Blk• Design  System React](https://demos.creative-tim.com/blk-design-system-react). I used their work because it provided me with a realistic and functional React application, completely designed too, which allowed me to speed up my work on the security aspects.

# Author

Liran Tal <liran.tal@gmail.com>
