# Running Nginx in Docker


## Step 1: Navigate to Project Directory

Change to the directory containing your website files

```bash
cd ~/Downloads/Nova-Bootstrap5_beta1-1.0.0
pwd
ls
````

Verify that required files such as `index.html`, `assets`, or other static resources are present.

<img width="1918" height="1122" alt="Screenshot from 2026-02-12 17-04-31" src="https://github.com/user-attachments/assets/d1e3fc94-e4a5-465b-9491-29954cc298f1" />

## Step 2: Run the Nginx Container

Launch the Nginx container in detached mode and mount the current directory as the web root.

```bash
sudo docker run -d \
  --name nova-nginx \
  -p 8080:80 \
  -v $(pwd):/usr/share/nginx/html \
  nginx:alpine
```

<img width="1918" height="1122" alt="Screenshot from 2026-02-12 17-07-00" src="https://github.com/user-attachments/assets/e8d44a7b-5883-46c3-b5d7-90e02b46d13c" />

### Command Explanation

| Option                            | Description                              |
| --------------------------------- | ---------------------------------------- |
| `-d`                              | Runs the container in detached mode      |
| `--name nova-nginx`               | Assigns a name to the container          |
| `-p 8080:80`                      | Maps host port 8080 to container port 80 |
| `-v $(pwd):/usr/share/nginx/html` | Mounts the current directory             |
| `nginx:alpine`                    | Uses the lightweight Nginx Alpine image  |

---

## Step 3: Verify Container Status

Check if the container is running.

```bash
docker ps
```

Ensure the container status is `Up` and the port mapping is correct.

---

## Step 4: Access the Application

Open a web browser and navigate to:

```
http://localhost:8080
```

The website should load if the container and volume mounting are configured correctly.

---

## Step 5: List Docker Images

View available Docker images.

```bash
docker images
```

Confirm that the `nginx:alpine` image is present.

---

## Step 6: Verify Mounted Files

Confirm that the project files exist in the directory.

```bash
ls
```

---

## Stopping the Container

```bash
docker stop nova-nginx
```

---

## Removing the Container

```bash
docker rm nova-nginx
```

---

## Verify Container Removal

```bash
docker ps -a
```

No containers should be listed after removal.
