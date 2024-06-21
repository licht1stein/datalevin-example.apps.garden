# [datalevin-example.apps.garden](https://datalevin-example.apps.garden)

A demo for setting up [datalevin](https://github.com/juji-io/datalevin?tab=readme-ov-file#datalevin) within [application.garden](https://application.garden) projects.


## Deploy Strategy
When using file storage back-end, app must be restarted on re-deploy, otherwise you'll see resource unavailable errors or similar:

`Platform constant error code: EAGAIN Resource temporarily unavailable (11)`

Make sure to include `:deploy-strategy :restart` in your `garden.edn` file.

## JVM Opts
These JVM opts are required for Datalevin to access the file storage, make sure to include them in `:nextjournal/garden` alias in `deps.edn`:

```clojure

:jvm-opts ["--add-opens=java.base/java.nio=ALL-UNNAMED"                                         "--add-opens=java.base/sun.nio.ch=ALL-UNNAMED"]

```

You can find more details in the Datalevin's [install docs](https://github.com/juji-io/datalevin/blob/master/doc/install.md#clojure-library).
