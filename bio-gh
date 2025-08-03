package main

import (
	"encoding/json"
	"fmt"
	"log"
	"net/http"
	"os/exec"
	"strings"
)

// User represents the JSON structure for GitHub public profile
type User struct {
	Bio string `json:"bio"`
}

func main() {
	// Get the currently authenticated GitHub username using GitHub CLI
	output, err := exec.Command("gh", "api", "https://api.github.com/user", "--jq", ".login").Output()
	if err != nil {
		log.Fatalf("Failed to retrieve GitHub username using gh CLI: %v", err)
	}
	username := strings.TrimSpace(string(output)) // Remove trailing newline

	// Fetch the public profile data of the user
	resp, err := http.Get("https://api.github.com/users/" + username)
	if err != nil {
		log.Fatalf("Failed to fetch user data from GitHub API: %v", err)
	}
	defer resp.Body.Close()

	var user User
	if err := json.NewDecoder(resp.Body).Decode(&user); err != nil {
		log.Fatalf("Failed to decode JSON response: %v", err)
	}

	// Print the user's GitHub bio
	fmt.Println(user.Bio)
}
