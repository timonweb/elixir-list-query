# ListQuery

**ListQuery** is a lightweight Elixir library designed to make building dynamic [Ecto](https://hexdocs.pm/ecto/Ecto.html) queries from API parameters simple and flexible.

Ecto’s query API is powerful, but constructing dynamic queries based on user input or API parameters can quickly become verbose and repetitive. **ListQuery** lets you transform provided params and options directly into Ecto-compatible queries, making your controllers and data-loading functions much cleaner.

With **ListQuery**, you can:
- Seamlessly convert user params into dynamic Ecto queries.
- Reuse a consistent querying pattern across multiple controllers or contexts.

> **Note:** If you’re exposing this pattern in an environment where you don’t trust all input, make sure to sanitize params to avoid leaking sensitive data or exposing unwanted query capabilities.

---

## Minimal Usage Example

```elixir
# Example: Fetching records with dynamic filters

def all_cycles(params \\ %{}, opts \\ []) do
  query = ListQuery.get_query(Cycle, params, opts)
  Repo.all(query)
end

# Usage:
all_cycles(%{"active" => "true", "owner_id" => "123"})
```

Just pass your params map (for example, from query params or a controller) and any options. ListQuery turns them into an Ecto query ready for use with your Repo.

## Attribution

This library is extracted from [`okr_app_pub`](https://github.com/sb8244/okr_app_pub/blob/master/lib/okr_app/query/list_query.ex), originally written by [Stephen Bussey](https://github.com/sb8244).  
All credit for the original implementation and idea goes to Stephen.  
If you use or modify this code, please provide appropriate attribution.
