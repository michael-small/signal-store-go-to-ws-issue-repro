# Go to Definition in Webstorm with NGRX Signal Store Issue Reproduction

Source repo: https://github.com/monsterlessonsacademy/monsterlessonsacademy/tree/413-ngrx-signals

## Issue: When going to the definition of a method (Go to Definition, F12, control click etc), rather than go to the method declaration in the signal store, it goes to some internal ngrx signal store package file in `node_modules`

## Recreate

1) Checkout `main` 
2) Open `src/app/posts/posts.component.ts`
3) Go to line 96: `this.store.addPost(this.addForm.getRawValue().title);`
4) `Go to Declaration` the `addPosts` method
5) On my PC and Macbook, it goes to a file `ts-helpers.d.ts`.
   - A node modules path from inside signal store, `node_modules/@ngrx/signals/src/ts-helpers.d.ts`

## Interesting case where it works as intended

## Recreate

1) Checkout `works-for-some-reason`
2) Open `src/app/posts/posts.component.ts`
3) Go to line 96: `this.store.addPost(this.addForm.getRawValue().title);`
4) `Go to Declaration` the `addPosts` method
