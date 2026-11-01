# Lab · S3 protection and lifecycle design

**Goal:** Create a protection plan for a fictional bucket without creating a bucket.

1. Classify data as public asset, active application object, backup, or archive.
2. For each category, state who needs read/write access and which account owns the data.
3. Choose a storage class using access frequency and retrieval expectations.
4. Decide whether versioning, replication, retention controls, lifecycle expiration, and encryption are needed.
5. Identify how the design prevents accidental public access.
6. Estimate cost categories to investigate: storage, requests, retrieval, replication, and data transfer.
7. Write a restore test that proves the required objects can be recovered.

**Expected result:** A short design decision record with explicit retention and recovery assumptions. Never use real sensitive data in this exercise.
