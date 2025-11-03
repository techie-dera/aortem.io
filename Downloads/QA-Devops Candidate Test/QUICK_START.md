# Quick Start Guide - Firebase Web App Docker Deployment

## Environment Setup

## Opened the Sample App Folder
```bash 
"cd firebase-dart-admin-auth-sdk-flutter-web-app"
```


## Verified Local Flutter Web Build
```bash
   "flutter run -d chrome"
   ```
## Confirmed the app launched in Chrome and rendered correctly.

### Build
```bash
cd "firebase-dart-admin-auth-sdk-flutter-web-app"
docker build --no-cache -t firebase-web-app-demo . > build_output.log 2>&1
```

### Monitor Build
```bash
tail -f build_output.log
```

### Run Container
```bash
# Detached mode (recommended)
docker run -d -p 8080:8080 --name firebase-web-app firebase-web-app-demo

# Or with logs to file
docker run -p 8080:8080 firebase-web-app-demo > run_output.log 2>&1
```

### Check Status
```bash
# Is container running?
docker ps

# View logs
docker logs -f firebase-web-app

# Check app
open http://localhost:8080
```

### Stop Container
```bash
docker stop firebase-web-app
docker rm firebase-web-app
```

## 🔍 Troubleshooting

### Build Failed?
```bash
# Check logs
cat build_output.log | grep -i error

# Clean and retry
docker system prune -a
docker build --no-cache -t firebase-web-app-demo .
```

### Port Already in Use?
```bash
# Use different port
docker run -d -p 8081:8080 --name firebase-web-app firebase-web-app-demo
```

### Container Crashes?
```bash
# Check logs
docker logs firebase-web-app

# Run interactively
docker run -it firebase-web-app-demo /bin/sh
```

##  Test Checklist

- [ ] Docker Desktop running
- [ ] Build completed without errors
- [ ] Image shows in `docker images`
- [ ] Container starts successfully
- [ ] http://localhost:8080 loads
- [ ] Server logs show "Server running on port 8080"
- [ ] App renders correctly in browser

## Expected Results

**Build Time:** 1-2 minutes  
**Image Size:** 50-150 MB  
**Container Port:** 8080  
**App URL:** http://localhost:8080

Runtime should show:
- `Server running on port 8080`
- No error messages
