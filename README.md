This repo outlines a bug I ran into with the [`@nx-plus/vue`](https://www.npmjs.com/package/@nx-plus/vue) package, that
does not occur with the Vue CLI

Link to GitHub issue upstream: (TO ADD)

# Setup

To get each project running (and see the bug present), `cd` into the relevant project and run `npm i`

# Bug

It seems, that if you use a typed property in a TypeScript Vue component:

```typescript
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'NotifCardBase',
  props: {
    soundUrl: {
      type: String
    },
  },
  setup(props) {
    function test(val: string) {return val};

    test(props.soundUrl);
  }
})
```

It will throw an error during `npm start`.

```
 DONE  Compiled successfully in 6238ms
                                                          11:21:56 PM


  App running at:
  - Local:   http://localhost:8080/
  - Network: http://192.168.1.127:8080/

  Note that the development build is not optimized.
  To create a production build, run nx build my-app --prod.

ERROR in apps/my-app/src/NotifCardBase.vue:31:12
TS2345: Argument of type 'unknown' is not assignable to parameter of type 'string'.
    29 |       function test(val: string) {return val};
    30 |
  > 31 |       test(props.soundUrl);
       |            ^^^^^^^^^^^^^^
    32 |     }, {
    33 |       immediate: true
    34 |     });

Terminate batch job (Y/N)? Y
```
