# Go to Definition in Webstorm with NGRX Signal Store Issue Reproduction

- Source repo I found an example on since I can't link my real project: https://github.com/monsterlessonsacademy/monsterlessonsacademy/tree/413-ngrx-signals
- Same on the two different computers which specs I will DM

## Issue: When going to the definition of a method (Go to Definition, F12, control click etc), rather than go to the method declaration in the signal store, it goes to some internal ngrx signal store package file in `node_modules`

### Recreate

1) Checkout `main` 
2) Open `src/app/posts/posts.component.ts`
3) Go to line 96: `this.store.addPost(this.addForm.getRawValue().title);`
4) `Go to Declaration` the `addPosts` method
5) On my PC and Macbook, it goes to a file `ts-helpers.d.ts`.
   - A node modules path from inside signal store, `node_modules/@ngrx/signals/src/ts-helpers.d.ts`

## Interesting case where it works as intended

For some reason, going to the definition seems fine when the store is small enough. 
Try deleting various methods and other things like the `withHooks` or `withComputed` 
and other methods, and at some point you can jump to `addPost` just fine.

I don't think it is related to any one given thing being removed as I toy around with this.
At some size small enough for the whole store in lines it just kind of works.

### Recreate

1) Checkout `works-for-some-reason`
2) Open `src/app/posts/posts.component.ts`
3) Go to line 84: `this.store.addPost(this.addForm.getRawValue().title);`
4) `Go to Declaration` the `addPosts` method
5) On my PC and Macbook, it goes to the correct spot where `addPosts` is declared

## Specs

Please DM @MichaelSmallDev on Twitter
