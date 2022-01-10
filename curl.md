# cURL
## Examples
### JSON with Headers

  ```sh
    # Set up URL and data
    env_url="https://jsonplaceholder.typicode.com/posts"
    sid='123'
    data='{ "sessionId": "'"$sid"'" }'

    # Post
    curl -i --location --request POST "$env_url" \
    --header 'Content-Type: application/json' \
    --data-raw "$data"
  ```
