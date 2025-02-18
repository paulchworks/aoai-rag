![image](https://github.com/user-attachments/assets/e500d34a-3436-4ba2-9b88-6565ce5ecbc2)


# Full-Stack Application Setup Script

The start.sh file automates the process of restoring dependencies, building the frontend, and starting the backend server for a full-stack application. It is designed to streamline the development workflow by handling common tasks in a single command.

## Overview of the Script

1. **Restore Frontend Dependencies**:
   - The script navigates into the `frontend` directory and runs `npm install` to restore all required npm packages.
   - If the installation fails, the script will exit with an error message.

2. **Build the Frontend**:
   - After successfully restoring the dependencies, the script builds the frontend using `npm run build`.
   - If the build process fails, the script will exit with an error message.

3. **Load Environment Variables**:
   - The script loads environment variables by sourcing the `loadenv.sh` script located in the `scripts` directory. This ensures that necessary configurations are available for the backend.

4. **Start the Backend**:
   - Finally, the script starts the backend server using Quart (a Python ASGI web framework) with the specified host and port (`127.0.0.1:50505`) and enables auto-reloading for development purposes.
   - If the backend fails to start, the script will exit with an error message.

## Prerequisites

Before running this script, ensure the following:

- **Node.js and npm**: Installed on your system to handle frontend dependencies and build processes.
- **Python**: Installed with Quart and other required dependencies for the backend.
- **Environment Variables**: Ensure the `scripts/loadenv.sh` file exists and contains the necessary environment variables for the backend.

## Usage

1. Save this script as `start.sh` (or any name you prefer).
2. Make the script executable:
   ```bash
   chmod +x start.sh
   ```
3. Run the script:
   ```bash
   ./start.sh
   ```

## Error Handling

The script includes error handling to ensure that issues during any step (e.g., dependency restoration, frontend build, or backend startup) are reported, and the process halts to prevent further execution with incomplete setup.

## Notes

- **Development Mode**: The backend is started with the `--reload` flag, which is suitable for development but should be disabled in production environments.
- **Port Configuration**: The backend listens on `127.0.0.1:50505`. Modify the `--port` and `--host` flags if you need a different configuration.
- **Customization**: Adjust paths (e.g., `frontend`, `scripts/loadenv.sh`) if your project structure differs.

## Troubleshooting

- **Frontend Build Failures**: Ensure all required dependencies are listed in `frontend/package.json` and that there are no syntax errors in the code.
- **Backend Startup Issues**: Verify that all required Python dependencies are installed and that the environment variables in `loadenv.sh` are correctly configured.

---

By running this script, you can efficiently set up and start your full-stack application with minimal manual intervention.
