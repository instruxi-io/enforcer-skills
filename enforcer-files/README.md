# /enforcer-files

Object storage via presigned URLs with support for resource sharing.

## When to use
- Building file upload or download features
- Generating presigned URLs for direct client-side transfers
- Sharing files between users via resource sharing intents
- Working with S3, GCS, or Storj backends

## What it covers
- Presigned URL generation for upload and download
- Multi-backend support (S3, GCS, Storj)
- Resource sharing intents between users
- File metadata and listing
- Tenant-scoped storage paths

## Tips
- Uploads go directly from the client to storage via presigned URLs; the server never proxies file bytes
- Storage paths are scoped by instance, tenant hash, and user ID
- Resource sharing intents grant time-limited access to another user's files
- Legacy per-user bucket fallback exists for backward compatibility
