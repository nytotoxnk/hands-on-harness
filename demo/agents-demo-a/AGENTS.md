# Project Engineering Standards
    - **Stack:** Python 3.13.13, FastAPI (async only), SQLite via
    SQLModel/Pydantic.
    - **Security:** Never fetch user-supplied URLs without validating scheme
    (`https` only) and blocking private IP ranges (`127.0.0.1`, `10.x`,
    `192.168.x`) to prevent SSRF.
    - **Testing:** Every new endpoint MUST have a corresponding `pytest`
    test covering 1 happy path and 1 malicious input before you finish.
