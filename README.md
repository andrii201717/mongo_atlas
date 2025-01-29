# Тестовая коллекция в mongo atlas  sample_mflix.theaters
Найти все кинотеатры в Калифорнии и посчитать их количество 


[
  {
    $match: {
      "location.geo": {
        $geoWithin: {
          $geometry: {
            type: "Polygon",
            coordinates: [
              [
                [
                  -117.34718924561263,
                  32.15329294025463
                ],
                [
                  -114.50141638995434,
                  32.420775070445984
                ],
                [
                  -114.53654621135684,
                  34.84987503195418
                ],
                [
                  -120.0173022725061,
                  39.08914107909818
                ],
                [
                  -119.9821697706655,
                  41.86956082699455
                ],
                [
                  -124.47919969764997,
                  41.97419413216579
                ],
                [
                  -125.2169929580545,
                  40.172158454535946
                ],
                [
                  -122.72254780124011,
                  36.421282443649496
                ],
                [
                  -120.2983676481069,
                  33.89230453271594
                ],
                [
                  -117.34718924561263,
                  32.15329294025463
                ]
              ]
            ]
          }
        }
      }
    }
  },
  {
    $count:
      /**
       * Provide the field name for the count.
       */
      "count_rest"
  }
]

{
  "count_rest": 170
}

Тестовая коллекция в mongo atlas  sample_airbnb.listingsAndReviews

Найти недвижимость с самым большим количеством спален (bedrooms) и напишите ее название 

name: "Venue Hotel Old City"

[
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        bedrooms: -1
      }
  },
  {
    $limit:
      /**
       * Provide the number of documents to limit.
       */
      1
  },
  {
    $project:
      /**
       * specifications: The fields to
       *   include or exclude.
       */
      {
        name: 1
      }
  }
]


Тестовая коллекция в mongo atlas  sample_airbnb.listingsAndReviews
Найти недвижимость с самым высоким рейтингом  review_scores_rating при минимальном количестве отзывов 50 (number_of_reviews) и напишите ее название 

name: "Ribeira Charming Duplex"
[
  {
    $sort:
      /**
       * Provide any number of field/order pairs.
       */
      {
        review_scores_rating: -1
      }
  },
  {
    $match:
      /**
       * query: The query in MQL.
       */
      {
        number_of_reviews: {
          $gte: 50
        }
      }
  },
  {
    $limit:
      /**
       * Provide the number of documents to limit.
       */
      1
  }
]

