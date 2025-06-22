<h1 align="center">
    <img width="25%" alt="Sasses" src="../../assets/images/logo/Sasses/SVG/SassesText - Solid.svg" />
    <br>
    Throw Module
</h1>

<p align="center">
    <strong>Provides Sass mixins and functions to standardize exception messages.</strong>
</p>

<p align="center">
    <a href="https://www.npmjs.com/package/@sasses/throw"><img alt="Version" src="https://img.shields.io/npm/v/%40sasses%2Fthrow"/></a>
    <a href="https://www.npmjs.com/package/@sasses/throw"><img alt="License" src="https://img.shields.io/github/license/officialxviid/sasses"/></a>
</p>

<h2>Getting Started</h2>

<h3>Require</h3>
<p>
    <ul>
        <li>Dart Sass: <code>>= 1.23.0</code></li>
    </ul>
</p>

<h3>Installation</h3>

<h4>Node Package Manager (NPM)</h4>

```bash
npm i @sasses/throw
```

<h3>How to Use</h3>

<p>Use the package like any other Sass module:</p>

```scss
@use "@sasses/throw";
```

<p>If you are not using the Sass <a href="https://sass-lang.com/documentation/js-api/classes/nodepackageimporter/">Node.js package importer</a>, you may need to include the full path name:</p>

```scss
// This is only an example, your path may be different
@use "../node_modules/sasses/throw";
```

<p>Depending on your setup, you may need to configure <code>node_modules</code> as include path:</p>

```js
const sass = require("sass");

sass.compile(filePath, {
  loadPaths: ["node_modules"],
});
```

<h2>Documentation</h2>

<p>See <a href="https://github.com/officialxviid/sasses/wiki/Throw-Package">Wiki page</a> for more information about this module.</p>

<hr>

<p align="center">
    <a href="https://x.com/officialxviid"><img alt="Twitter/X" src="https://img.shields.io/twitter/follow/officialxviid?style=plastic&logo=x&label=@officialxviid"></a>
    <a href="https://github.com/officialxviid"><img alt="GitHub" src="https://img.shields.io/github/followers/officialxviid?style=plastic&logo=github&label=officialxviid"></a>
    <a href="https://x.com/officialxviid"><img alt="Mastodon" src="https://img.shields.io/mastodon/follow/114727602765291531?style=plastic&logo=mastodon&label=@xviid"></a>
    <a href="https://xviid.net/teams/sassdev"><img alt="Dev" src="https://img.shields.io/badge/XVIID%20Sass%20Dev-0c91f0?logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyBpZD0iTGF5ZXJfMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2aWV3Qm94PSIwIDAgNjQgNjQiPgogIDxkZWZzPgogICAgPHN0eWxlPgogICAgICAuY2xzLTEgewogICAgICAgIGZpbGw6ICNmZmY7CiAgICAgIH0KCiAgICAgIC5jbHMtMiB7CiAgICAgICAgZmlsbC1ydWxlOiBldmVub2RkOwogICAgICB9CgogICAgICAuY2xzLTIsIC5jbHMtMyB7CiAgICAgICAgZmlsbDogI2ZmZjsKICAgICAgfQogICAgPC9zdHlsZT4KICA8L2RlZnM+CiAgPGc+CiAgICA8cGF0aCBmaWxsPSIjZmZmIiBkPSJNMzEuNjUsMjYuOTJzLTIuNzgtLjMyLTQuOTMsMmMtMi4xNSwyLjMyLTguNzEsMTAuNTItOS4xOSwxMS4yOC0uNDcuNzYtMS42MywzLjExLDAsNi43NSwxLjYzLDMuNjQsNS41Niw0LjAxLDUuNTYsNC4wMSwwLDAsMi42MS43NSw0Ljk0LTEuMDdsMi4xOC04LjhjLTEuMDEtLjU5LTEuNjMtMS43MS0xLjYzLTIuOTMsMC0xLjg1LDEuMzUtMy4zNSwzLjEtMy4zNXMzLjE3LDEuNSwzLjE3LDMuMzVjMCwxLjIyLS42MywyLjM0LTEuNjMsMi45M2wyLjE4LDguOGMyLjM0LDEuODIsNC45NCwxLjA3LDQuOTQsMS4wNywwLDAsMy45NC0uMzcsNS41Ni00LjAxLDEuNjMtMy42NC40Ny01Ljk4LDAtNi43NS0uNDctLjc2LTcuMDMtOC45Ni05LjE5LTExLjI4LTIuMTUtMi4zMi01LjA3LTItNS4wNy0yWiIvPgogICAgPGVsbGlwc2UgZmlsbD0iI2ZmZiIgY3g9IjM4LjczIiBjeT0iMTkuNTMiIHJ4PSI2LjYxIiByeT0iNC45NSIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTMuMjggNTQuNjYpIHJvdGF0ZSgtODAuODMpIi8+CiAgICA8ZWxsaXBzZSBmaWxsPSIjZmZmIiBjeD0iNDguMjYiIGN5PSIyOS45NyIgcng9IjYuNjEiIHJ5PSI0Ljk1IiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMC45OCA3Mi44Mykgcm90YXRlKC04MC44MykiLz4KICAgIDxlbGxpcHNlIGZpbGw9IiNmZmYiIGN4PSIyNS4yNyIgY3k9IjE5LjQ2IiByeD0iNC45NSIgcnk9IjYuNjEiIHRyYW5zZm9ybT0idHJhbnNsYXRlKC0yLjc4IDQuMjgpIHJvdGF0ZSgtOS4xNykiLz4KICAgIDxlbGxpcHNlIGZpbGw9IiNmZmYiIGN4PSIxNS43NCIgY3k9IjI5Ljg5IiByeD0iNC45NSIgcnk9IjYuNjEiIHRyYW5zZm9ybT0idHJhbnNsYXRlKC00LjU2IDIuODkpIHJvdGF0ZSgtOS4xNykiLz4KICA8L2c+CiAgPGc+CiAgICA8cGF0aCBmaWxsPSIjZmZmIiBkPSJNMzIsNjRjLTIuNDYsMC00LjkxLS4yOC03LjMtLjg1LTIuMzYtLjU1LTQuNjYtMS4zOC02LjgzLTIuNDYtMi4xNy0xLjA3LTQuMjMtMi40LTYuMS0zLjk0LTEuOS0xLjU2LTMuNjItMy4zNC01LjEyLTUuMjktLjQ3LS42MS0uMzUtMS40OS4yNS0xLjk2LjYxLS40NywxLjQ4LS4zNiwxLjk1LjI1LDUuNDksNy4xNywxNC4xNSwxMS40NCwyMy4xNSwxMS40NHMxNy42Ni00LjI4LDIzLjE1LTExLjQ0Yy40Ny0uNjEsMS4zNC0uNzIsMS45NS0uMjUuNjEuNDcuNzIsMS4zNS4yNSwxLjk2LTEuNSwxLjk1LTMuMjIsMy43My01LjEyLDUuMjktMS44OCwxLjU0LTMuOTMsMi44Ni02LjEsMy45NHMtNC40NywxLjktNi44MywyLjQ2Yy0yLjM5LjU2LTQuODQuODUtNy4zLjg1WiIvPgogICAgPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTMuNyw0NC45OGMtLjU1LDAtMS4wNi0uMzMtMS4yOS0uODYtMS42LTMuOS0yLjQyLTguMDItMi40Mi0xMi4yNSwwLTMuOTUuNzEtNy44MSwyLjEtMTEuNDcsMS4zNi0zLjU2LDMuMzEtNi44Miw1LjgyLTkuNywyLjUxLTIuODgsNS40Ny01LjI2LDguOC03LjA3QzIwLjE2LDEuNzUsMjMuODcuNTMsMjcuNzcuMDFjLjc2LS4xLDEuNDYuNDMsMS41NiwxLjIuMS43Ni0uNDMsMS40Ny0xLjE5LDEuNTdDMTMuNjgsNC43MSwyLjc4LDE3LjIyLDIuNzgsMzEuODdjMCwzLjg2Ljc0LDcuNjIsMi4yMSwxMS4xOC4yOS43MS0uMDUsMS41My0uNzYsMS44Mi0uMTcuMDctLjM1LjExLS41My4xMVoiLz4KICAgIDxwYXRoIGZpbGw9IiNmZmYiIGQ9Ik02MC4zLDQ0Ljk4Yy0uMTgsMC0uMzYtLjAzLS41My0uMTEtLjcxLS4yOS0xLjA1LTEuMTEtLjc2LTEuODIsMS40Ni0zLjU2LDIuMi03LjMzLDIuMi0xMS4xOCwwLTE0LjY1LTEwLjktMjcuMTUtMjUuMzYtMjkuMDktLjc2LS4xLTEuMy0uOC0xLjE5LTEuNTcuMS0uNzYuOC0xLjMsMS41Ni0xLjIsMy45LjUyLDcuNjEsMS43NCwxMS4wNSwzLjYxLDMuMzMsMS44Miw2LjI5LDQuMiw4LjgsNy4wNywyLjUxLDIuODcsNC40Niw2LjE0LDUuODIsOS42OSwxLjQsMy42NywyLjEsNy41MywyLjEsMTEuNDcsMCw0LjIyLS44MSw4LjM0LTIuNDEsMTIuMjUtLjIyLjU0LS43NC44Ni0xLjI5Ljg2WiIvPgogIDwvZz4KPC9zdmc+"/></a>
</p>
