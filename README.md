### Summary:

Implement an API in Javascript using Express API framework and NodeJs that fetches and publishes tweets using Twitter APIs.

### Prerequisites:
1.  NodeJs
2.  Express
3.  Mocha or Chai (Test frameworks)
4.  Twitter Account


### Tasks:

Implement the following endpoints and their requirements:

1. **GET** `/mytwitterapi/mytweets?page=1`

  - Return **top 10** tweets of authenticated user.
  - Paginate results by providing `page` request parameter.
  - Response must have the following structure:
  ```json
  {
      "tweets": [
        {
          "id": 12345456566,
          "text": "Hey @someuser check this out http://t.co/78pYTvWfJd #ThisIsAwesome",
          "createdOn": "2018-01-16T00:00Z+00:00",
          "user": {
            "id": 6253282,
            "name": "Twitter Bot",
            "screen_name": "twitterbot",
            "location": "London, UK",
            "description": "I fetch any tweets!!",
            "url": "http://t.co/78pYTvWfJd"
          },
          "user_mentions": [
            {
              "screen_name": "someuser",
              "name": "Some User",
              "id": "850007368138018816"
            }
          ],
          "urls": [
            {
              "url": "http://t.co/78pYTvWfJd",
              "expanded_url": "https://someurl.com",
              "display_url": "someurl.com"
            }
          ]
        }
      ],
      "meta": {
        "page": 1
      }
  }
  ```
2. **GET** `/mytwitterapi/timeline/<screen_name>?page=1`
  - Return **top 10** tweets of the provided `screen_name`.
  - Paginate results by providing `page` request parameter.
  - Response must have the following structure:

  ```json
  {
      "tweets": [
        {
          "id": 12345456566,
          "text": "Hey @someuser check this out http://t.co/78pYTvWfJd #ThisIsAwesome",
          "createdOn": "2018-01-16T00:00Z+00:00",
          "user": {
            "id": 6253282,
            "name": "Twitter Bot",
            "screen_name": "twitterbot",
            "location": "London, UK",
            "description": "I fetch any tweets!!",
            "url": "http://t.co/78pYTvWfJd"
          },
          "user_mentions": [
            {
              "screen_name": "someuser",
              "name": "Some User",
              "id": "850007368138018816"
            }
          ],
          "urls": [
            {
              "url": "http://t.co/78pYTvWfJd",
              "expanded_url": "https://someurl.com",
              "display_url": "someurl.com"
            }
          ]
        }
      ],
      "meta": {
        "page": 1
      }
  }
  ```
3. **GET** `/mytwitterapi/mentions/<screen_name>?page=1`
  - Return **top 10** tweets mentioning `screen_name`.
  - Paginate results by providing `page` request parameter.
  - Response must have the following structure:

  ```json
  {
      "tweets": [
        {
          "id": 12345456566,
          "text": "Hey @someuser check this out http://t.co/78pYTvWfJd #ThisIsAwesome",
          "createdOn": "2018-01-16T00:00Z+00:00",
          "user": {
            "id": 6253282,
            "name": "Twitter Bot",
            "screen_name": "twitterbot",
            "location": "London, UK",
            "description": "I fetch any tweets!!",
            "url": "http://t.co/78pYTvWfJd"
          },
          "user_mentions": [
            {
              "screen_name": "someuser",
              "name": "Some User",
              "id": "850007368138018816"
            }
          ],
          "urls": [
            {
              "url": "http://t.co/78pYTvWfJd",
              "expanded_url": "https://someurl.com",
              "display_url": "someurl.com"
            }
          ]
        }
      ],
      "meta": {
        "page": 1
      }
  }
  ```
4. **POST** `/mytwitterapi/new`
  - Publish a new tweet using the following request body:

  ```json
  {
      "text":  "This is my new tweet @twitterbot #APIAreFun"
  }
  ```
  - Return newly created tweet. It must have the following structure:

  ```json
  {
      "id": 12345456566,
      "text": "This is my new tweet @twitterbot #APIAreFun",
      "createdOn": "2018-01-16T00:00Z+00:00",
      "user": {
        "id": 6253282,
        "name": "Twitter Bot",
        "screen_name": "twitterbot",
        "location": "London, UK",
        "description": "I fetch any tweets!!",
        "url": "http://t.co/78pYTvWfJd"
      },
      "user_mentions": [
        {
          "screen_name": "twitterbot",
          "name": "Twitter API",
          "id": "850007368138018816"
        }
      ]
  }
  ```
  - Make sure new tweets do not exceed 140 characters. Respond with an 400 error otherwise:

  ```json
  {
      "error": "Tweets must not exceed 140 characters"
  }
  ```
