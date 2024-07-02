
User Collection:
{
  "_id": ObjectId,
  "username": String,
  "email": String,
  "password_hash": String,
  "created_at": Date,
  "last_login": Date,
  "preferences": {
    "favorite_genres": [String],
    "favorite_authors": [String]
  },
  "reading_lists": {
    "currently_reading": [ObjectId], // References to Manga documents
    "want_to_read": [ObjectId],
    "already_read": [ObjectId]
  },
  "friends": [ObjectId], // References to other User documents
  "notifications": [
    {
      "type": String, // e.g., "new_chapter", "recommendation"
      "message": String,
      "created_at": Date,
      "read": Boolean
    }
  ]
}

Manga Collection:
{
  "_id": ObjectId,
  "title": String,
  "original_title": String,
  "author": String,
  "description": String,
  "genres": [String],
  "themes": [String],
  "status": String, // e.g., "Ongoing", "Completed"
  "publication": {
    "start_date": Date,
    "end_date": Date
  },
  "chapter_number": Number,
  "cover_image_url": String,
  "external_links": [
    {
      "site_name": String,
      "url": String
    }
  ],
  "average_rating": Number,
  "updated_at": Date
}

Ratings Collection:
{
  "_id": ObjectId,
  "user_id": ObjectId,  // Reference to User document
  "manga_id": ObjectId,  // Reference to Manga document
  "rating": Number,  // Rating out of 10
  "created_at": Date,
  "updated_at": Date
}

UserInteractions Collection:
{
  "_id": ObjectId,
  "user_id": ObjectId, // Reference to User document
  "manga_id": ObjectId, // Reference to Manga document
  "interaction_type": String, // e.g., "view", "add_to_list", "rate"
  "timestamp": Date
}

RecommendationLogs Collection:
{
  "_id": ObjectId,
  "user_id": ObjectId, // Reference to User document
  "recommended_mangas": [
    {
      "manga_id": ObjectId, // Reference to Manga document
      "score": Number
    }
  ],
  "created_at": Date
}