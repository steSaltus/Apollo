# Apollo notes 

> For the mambo jumble staff, please see `graphql.org`.  I hear their documentation is great :)

<br />

If you're new to Apollo, you're going to find not knowing this very annoying.

1. Always include an id as part of your query because it's used for caching. Apollo is going to use 
   the path to the node based on the 
   query as an index to store it... and do the same with the mutation although in a different path. So No id no caching.

2. Don't use `await`. 

```
   await = useQuery(ACCOUNTS);
```

    Apollo provides a loading property already. Once the `useQuery` promise is resolved 
    and there's no errors, the data gets set; which causes the
    property to be updated with the data; which in turn causes a re-rendering of the entire component.
  
3. It's related to number two. Thus there's no need for `useState` or `useEffect` in most cases. 
   None for the loading state, for example. 

4. Last one Apollo client `useQuery` as it returns data back to the client, it also provides you with 
   2 more pieces of states: loading and error, 
   that must be set or your application would not work. In fact, it'll break.
   
  ````
  // do something like this
  
  if(loading) {
    return 'is loading..'
  }
  if(error) console.log(error);
  
  // along with the data
  
  data.accounts(acct => acct.name);
  
  ````
  
  ...because without setting them all up, what you get is a ridiculous error.
  
  
  
  ````
    ..blah blah of undefined   
  ````
  
  which isn't very helpful.  Same for `useMutation` but the syntax is a little different.
  
  
  
  
