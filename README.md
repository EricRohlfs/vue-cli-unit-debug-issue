# Issue and Workaround

Problem: Cannot debug unit tests when there is more than one unit test in the tests folder.

## Workaround

In the jest.config.js change the testMatch to point to a single test file.

Original - that does not work
```
  testMatch: [
    '**/tests/unit/**/*.spec.(js|jsx|ts|tsx)|**/__tests__/*.(js|jsx|ts|tsx)'
   ]
```

Workaround
```
  testMatch: [
    '**/tests/unit/HelloWorldSecondTest.spec.(js|jsx|ts|tsx)|**/__tests__/*.(js|jsx|ts|tsx)'
  ]
```



```
node --inspect-brk ./node_modules/@vue/cli-service/bin/vue-cli-service.js test:unit
```

## Steps to reproduce
1. Create a new project or just clone this repo and skip to step 5

```
vue create hello1
```

2. Choose manual config and add unit tests and choose Jest as the runner.

3. add debugger statement in the HelloWorld.js test file.

3. Run the current test to see if it works, using the node --inspect-brk command at the top of the page.

4. Add a new unit test in the tests/unit folder. (I just copied the existing test and changed a few strings)

5. Run the node --inspect-brk command again

Now the debugger does not stop on the debugger statements.

## Environment
Windows 10
Node 8.11
NPM 5.6
