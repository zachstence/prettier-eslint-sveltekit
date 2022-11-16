# Prettier ESLint and SvelteKit error repro

This repo reproduces an error occurring with the Prettier ESLint VSCode Extension and SvelteKit

## Reproduction steps
1. Clone and setup this repo
```sh
# Clone
git clone https://github.com/zachstence/prettier-eslint-sveltekit

# Install dependencies
npm i

# Open in VSCode
code prettier-eslint-sveltekit
```

3. Ensure you have the Prettier ESLint plugin installed in VSCode

4. Follow troubleshooting steps here

5. Observe error in the Output tab
```txt
Error: Cannot find module 'prettier-plugin-svelte'
Require stack:
- /home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js
- /home/zach/.vscode-server/extensions/esbenp.prettier-vscode-9.9.0/dist/extension.js
- /home/zach/.vscode-server/bin/6261075646f055b99068d3688932416f2346dd3b/out/vs/loader.js
- /home/zach/.vscode-server/bin/6261075646f055b99068d3688932416f2346dd3b/out/bootstrap-amd.js
- /home/zach/.vscode-server/bin/6261075646f055b99068d3688932416f2346dd3b/out/bootstrap-fork.js
	at Function.Module._resolveFilename (node:internal/modules/cjs/loader:933:15)
	at resolve (node:internal/modules/cjs/helpers:108:19)
	at /home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js:37165:25
	at Array.map (<anonymous>)
	at Object.load (/home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js:37160:65)
	at Object.load [as loadPlugins] (/home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js:15932:23)
	at /home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js:37227:24
	at Object.format (/home/zach/code/foss/prettier-eslint-sveltekit/node_modules/prettier/index.js:37243:12)
	at /home/zach/.vscode-server/extensions/rvest.vs-code-prettier-eslint-5.0.4/dist/extension.js:184:131
	at Lge (/home/zach/.vscode-server/extensions/rvest.vs-code-prettier-eslint-5.0.4/dist/extension.js:180:1160)
	at runMicrotasks (<anonymous>)
	at processTicksAndRejections (node:internal/process/task_queues:96:5)
```

## Check ESLint Configuration
1. Run `npx eslint --print-config .eslintrc.js` to check if ESLint configuration is valid
2. Observe that config prints successfully

## Try ESLint
1. Run `npx eslint src/routes/+page.svelte`
2. Observe that linting runs successfully

## Try `prettier-eslint-cli`
1. Run `npx prettier-eslint-cli src/routes/+page.svelte`
2. Observe that formatting completed successfully
```txt
<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
1 file was unchanged
```