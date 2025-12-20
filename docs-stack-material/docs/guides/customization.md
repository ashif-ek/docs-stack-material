# Customization

How to modify and extend the projects.

## Tailwind CSS Theme

Most styled projects use `tailwind.config.js`. You can customize:
*   **Colors**: Modify `theme.extend.colors` to change the palette.
*   **Fonts**: Update `fontFamily` settings.

## React Components

UI components are typically found in `src/components`.
*   **Reusability**: Components are built to be generic.
*   **Props**: Check the interface definitions (TypeScript) or PropTypes (JS) to understand available options.

## Backend Logic

*   **Django**: Apps are modular. To add specific business logic, create a new app: `python manage.py startapp <name>`.
*   **FastAPI**: Add new routers in the `api/` directory and include them in `main.py`.