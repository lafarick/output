package output

import (
	"database/sql"
	"fmt"

	_ "github.com/lib/pq"
)

type customer struct {
	id           int
	name         string
	phone_number string
	email        string
	city         string
	district     string
	street       string
	number       int
	apartment    int
}

func output() {
	var id int
	fmt.Println("Input the id of customer:")
	fmt.Scan(&id)
	connStr := "user=xyz password=1111 dbname=apelsin sslmode=disable"
	db, err := sql.Open("postgres", connStr)
	if err != nil {
		panic(err)
	}
	defer db.Close()
	rows, err := db.Query("select * from customers")
	if err != nil {
		panic(err)
	}
	defer rows.Close()
	customers := []customer{}

	for rows.Next() {
		c := customer{}
		err := rows.Scan(&c.id, &c.name, &c.phone_number, &c.email, &c.city, &c.district, &c.street, &c.number, &c.apartment)
		if err != nil {
			fmt.Println(err)
			continue
		}
		customers = append(customers, c)
	}
	for _, c := range customers {
		if id == c.id {
			fmt.Println(c.id, c.name, c.phone_number, c.email, c.city, c.district, c.street, c.number, c.apartment)
		}
	}
}
