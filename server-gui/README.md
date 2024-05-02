

## Build Process

### Dependencies

#### Server backend:

```sh
   sudo apt install curl gnupg software-properties-common
   sudo add-apt-repository universe
   sudo mkdir -p /etc/apt/keyrings
   curl -fsSL https://repo.jellyfin.org/jellyfin_team.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/jellyfin.gpg
   
   export VERSION_OS="$( awk -F'=' '/^ID=/{ print $NF }' /etc/os-release )"
   export VERSION_CODENAME="$( awk -F'=' '/^VERSION_CODENAME=/{ print $NF }' /etc/os-release )"
   export DPKG_ARCHITECTURE="$( dpkg --print-architecture )"
   cat <<EOF | sudo tee /etc/apt/sources.list.d/jellyfin.sources
   Types: deb
   URIs: https://repo.jellyfin.org/${VERSION_OS}
   Suites: ${VERSION_CODENAME}
   Components: main
   Architectures: ${DPKG_ARCHITECTURE}
   Signed-By: /etc/apt/keyrings/jellyfin.gpg
   EOF
   
   sudo apt update
   sudo apt install jellyfin-server
   ```

- [Node.js](https://nodejs.org/en/download)
- npm (included in Node.js)

### Getting Started

1. Install build dependencies in the project directory.

   ```sh
   npm install
   ```

3. Run the web client with webpack for local development.

   ```sh
   npm start
   ```

4. Build the client with sourcemaps available.

   ```sh
   npm run build:development
   ```
