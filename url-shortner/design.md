# system name: URL Shortner
## date: 12/03/2026
## version: 1


## Problem Statement
Design a system that converts long URLs into short URLs
and redirects users when they access the short link.

Example:
https://example.com/product/very-long-url

↓

short.ly/abc123

## End user benefit
• Easy sharing

• Clean URLs

• Custom links

• Click analytics


## Functional Rerquirements
1 Users can submit long URLs

2 System generates short URL

3 Short URL redirects to original URL

4 Store mapping between short and long URL

## Non Functional Requirements
Low latency (<50ms)

High availability

Massive scalability

Unique short URL generation

## Capacity Estimation
Example:

100M URLs per month

3.3M per day

Storage estimation

600GB per year

## High level Architecture
User

   |

Load Balancer

   |

Application Servers

   |

Cache (Redis)

   |

Database

## Database Design
TABLE: URL_MAPPING

| Column       | Type      |
| ------------ | --------- |
| id           | bigint    |
| short_code   | varchar   |
| original_url | text      |
| created_at   | timestamp |


## API Design
POST /shorten

GET /{shortCode}

Sample request:

{

"url":"https://example.com"

}

## Core Design Challenges
How to generate short URL?

How to avoid collisions?

How to scale redirects?

## Scaling Improvements
Redis cache

CDN

Sharding

Analytics pipeline

## Tradeoffs
Random key generation vs Base62 encoding

Database vs Cache lookups

Consistency vs performance

