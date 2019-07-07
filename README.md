# Spark-FollowerCount
This program in Scala analyzes a Twitter dataset of  50,000 users and calculates the number of followers for a particular user.

## Pseudo-code

    val textFile = sc.textFile(args(0))
    val counts = textFile.flatMap(line => line.split(",").tail)
                      .map(user_Id => (user_Id,1))
                      .reduceByKey(_ + _) counts.saveAsTextFile(args(1))

## Program Descroption

This program reads the input line by line, and splits the line based on a comma, and fetches the tail of the List generated after splitting. It does so using the flatmap function. The input is of the format “user_id_a,user_id_b”, which means user_id_a follows user_id_b. Hence, we need to map this as “user_id_b,1”, indicating user_id_b is followed by one user. The “line.split(“,”).tail” will fetch us the user_id_b from the given input and the map will then map it to “user_id_b,1”. The reduceByKey method will then sum up the value part for the keys, as inputted to it by the mapper and will generate the required “key,value” pair output as “user_id, total_no_of_followers”.
