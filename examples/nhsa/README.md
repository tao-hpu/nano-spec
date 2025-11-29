# NHSA Medical Insurance Data Integration

## Background
Integrate NHSA (National Healthcare Security Administration) public data from the collection team's `aidb_test` database to production `aidb`.

## Goals
- Sync core tables for drug/device/hospital data
- Establish data pipeline for ongoing updates
- Enable downstream features (drug search, hospital analysis)

## Scope

### In Scope
- Database table synchronization
- DDL analysis and migration
- Index optimization

### Out of Scope
- Frontend page development
- Backend API development
- Business feature implementation

## Dependencies
- [x] Collection team's DDL (`ybml_schema.sql`)
- [ ] Production database access
- [ ] Confirmation on sync frequency

## Resources
- DDL Source: `docs/ybml_schema.sql`
- NHSA Portal: https://fuwu.nhsa.gov.cn/nationalHallSt/
