# findcourt
algorithm for find court of Korea which matched with residence address

## Procedure
1. Kakao Address API Call with regidence address.
2. Getting "sido, sigungu" data from Kakao Address API.
3. Querying with "sido", "sigungu" to database.
- Stored data is not matched with "sigungu" for 100%.
- There is exception case of sigungu data.

- *Example*
- Query data : "sido":"서울", "sigungu":"고양시 덕양구"
- Stored data : "sido":"서울", "sigungu""고양시"
- [1] Query => select value from table where key="서울,고양시 덕양구" <br/>
- [2] Query => select value from table where key="서울,덕양구" <br/>
- [3] Query => select value from table where key="서울,고양시" <br/>
- [4] Query => select value from table where key="서울," <br/>
- Stored new data : "sido:"서울", "sigungu":"고양시 덕양구" => key


4. Return to Court, Support Court

## Stored Data
key: "sido,sigungu", value: ""highCourt:{{value}},court:{{value}},support:{{value}}"

### Software Stack
- [golang](https://golang.org/)
- [graphql-go: An implementation of GraphQL for Go / Golang](https://github.com/graphql-go/graphql)
- [Bolt is a pure Go key/value store inspired by Howard Chu's LMDB project.](https://github.com/boltdb/bolt)
