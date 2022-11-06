


## pages


+ 在不影响URL结构的情况下组织路由。  

+ 在布局中选择特定的路由段。  
	+ 文件夹下有自己的layout用自己的
	+ 没有就沿用 父级的layout

+ 通过拆分应用程序创建多个根布局

# Data Fetching: Caching | Next.js

![](https://beta.nextjs.org/static/twitter-cards/docs.png)

### Metadata

- Title: Data Fetching: Caching | Next.js
- Tags: #Next.js13
- URL: https://beta.nextjs.org/docs/data-fetching/caching
- Highlighted by: [reliable special](https://glasp.co/#/4jel7b547viqp01j/?p=FK5X24EIxJtdvc7Wnrxg)

### Highlights & Notes

- Segment-level caching allows you to cache and revalidate data used in route segments.
- lowest
-  cache and dedupe requests on a per-request basis.
- This is because getUser() is wrapped in cache(), so the second request can reuse the result from the first request.
- wrap functions
-  with cache
- It's a pattern, not an API.


# Data Fetching: Fundamentals | Next.js

![](https://beta.nextjs.org/static/twitter-cards/docs.png)

### Metadata

- Title: Data Fetching: Fundamentals | Next.js
- Tags: #Next.js13
- URL: https://beta.nextjs.org/docs/data-fetching/fundamentals
- Highlighted by: [reliable special](https://glasp.co/#/4jel7b547viqp01j/?p=Zf1HIRiskDxjWQ09R228)

### Highlights & Notes

-  getServerSideProps, getStaticProps, and getInitialProps are not supported in the new app directory.
- we recommend fetching data inside the Server Component that directly needs the data
- secure
- reduces both the back and forth communication
-  we recommend fetching data directly inside the Server Component that needs it instead of passing data down as props to other Server Components, even if you're requesting the same data in multiple components.
- Behind the scenes, React and Next.js will cache and dedupe requests to avoid the same data being fetched more than once.
- React extends fetch to provide automatic request deduping, and Next.js extends the fetch options object to allow each request to set its own caching and revalidating rules
- By default, Next.js automatically does static fetches
-  mark requests as dynamic
- the data will be fetched at request time and not cached.
- Together with component-level data fetching, this allows you to configure caching within your application code directly where the data is being used.
- that allow you to progressively render and incrementally stream rendered units of the UI to the client.


