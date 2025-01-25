## Objective

The goal is to learn how to:

- Write GraphQL queries to retrieve details of specific resources (e.g., episodes) by their unique ID.
- In the context of GraphQL and your project, a "**resource**" refers to an entity or object that you can query for data. Resources are typically defined in your GraphQL schema and can represent various types of data in your application. 

For example, in a GraphQL API for a TV show database, resources might include:

- **Episodes**: Individual episodes of a TV show, each with attributes like title, air date, and duration.
- **Characters**: Characters in the TV show, each with attributes like name, role, and episodes they appear in.

When you write GraphQL queries, you specify which resources you want to retrieve and what details you need about them. For instance, you might query for a specific episode by its unique ID or retrieve a list of characters with pagination to handle large datasets efficiently.

Here's a simple example of a GraphQL query to retrieve an episode by its ID:

```graphql
query GetEpisode($id: ID!) {
  episode(id: $id) {
    title
    airDate
    duration
  }
}
```

And an example of a query to retrieve paginated characters:

```graphql
query GetCharacters($first: Int, $after: String) {
  characters(first: $first, after: $after) {
    edges {
      node {
        name
        role
      }
    }
    pageInfo {
      endCursor
      hasNextPage
    }
  }
}
```

In these examples, `episode` and `characters` are resources, and the queries specify how to retrieve and handle data for these resources.
- Retrieve and handle paginated data for multiple resources (e.g., characters).

## Tasks and Learning Goals

### 1. Retrieve Episode Details

**What you’ll learn:** Writing queries for specific resources.

**Task:** Write a GraphQL query to fetch the details of a specific episode using the `episode(id: ID!)` field.

**Fields to retrieve:**
- `id`: The unique identifier of the episode.
- `name`: The title of the episode.
- `air_date`: The date the episode aired.
- `episode`: The episode code.

**File:** `episode/episode-page-1.graphql`

**Output:** The JSON response will be saved in `episode/characters-page-1-output.json`.

### 2. Retrieve Paginated Character Lists

**What you’ll learn:** Handling and paginating through lists of resources.

**Task:** Write GraphQL queries using the `characters(page: Int)` field to fetch lists of characters.

**Fields to retrieve:**
- `id`: The unique identifier of the character.
- `name`: The character’s name.
- `status`: The character's current status (e.g., Alive, Dead, Unknown).
- `image`: The URL of the character's image.

**Files and Outputs:**
- **Page 1:** `characters-page-1.graphql`, `characters-page-1-output.json`
- **Page 2:** `characters-page-2.graphql`, `characters-page-2-output.json`
- **Page 3:** `characters-page-3.graphql`, `characters-page-3-output.json`
- **Page 4:** `characters-page-4.graphql`, `characters-page-4-output.json`