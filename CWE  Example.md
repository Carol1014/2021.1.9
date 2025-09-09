For example:
@@VULNERABLE@@
@@CWE: CWE-1234@@

SECURITY VULNERABILITY CHECKLIST:

**Input Validation Vulnerabilities:**
- SQL injection via unsanitized user input - `CWE-89`
  Example: `"SELECT * FROM users WHERE id = '" + user_input + "'";`
- Command injection in system calls or subprocesses - `CWE-78`
  Example: `system("ping " + user_input);`
- XXE injection in XML parsing - `CWE-611`
  Example: `xmlDoc = xmlReadMemory(buffer, size, "noname.xml", NULL, 0);`
- Template injection in templating engines - `CWE-1336`
  Example: `template.render(user_input)`
- NoSQL injection in database queries - `CWE-943`
  Example: `db.users.find({$where: "this.name == '" + name + "'"})`
- Path traversal in file operations - `CWE-22`
  Example: `fopen("/var/www/files/" + filename, "r");`

**Authentication & Authorization Issues:**
- Authentication bypass logic - `CWE-288`
  Example: `if (user_id == 1) { grant_admin_access(); } // Magic number bypass`
- Privilege escalation paths - `CWE-269`
  Example: `setuid(0); system("/bin/bash"); // Without proper checks`
- Session management flaws - `CWE-613`/`CWE-384`
  Example: `session_id = get_cookie("session"); // No expiration check`
- JWT token validation vulnerabilities - `CWE-347`
  Example: `if (jwt.header.alg == "none") { accept_token(); }`
- Authorization logic bypasses - `CWE-862`
  Example: `// Front-end hides button but back-end has no permission check`

**Crypto & Secrets Management:**
- Hardcoded API keys, passwords, or tokens - `CWE-798`
  Example: `char* password = "supersecret123";`
- Weak cryptographic algorithms or implementations - `CWE-327`
  Example: `EVP_EncryptInit_ex(ctx, EVP_des_ecb(), NULL, key, iv); // Weak DES algorithm`
- Improper key storage or management - `CWE-321`
  Example: `unsigned char key[] = {0x01, 0x02, 0x03, ...}; // Hardcoded key`
- Cryptographic randomness issues - `CWE-338`
  Example: `int token = rand(); // Not cryptographically secure`
- Certificate validation bypasses - `CWE-295`
  Example: `SSL_CTX_set_verify(ctx, SSL_VERIFY_NONE, NULL); // Disabling cert verification`

**Injection & Code Execution:**
- Remote code execution via deserialization - `CWE-502`
  Example: `pickle.loads(user_data) // Python Pickle injection`
- Pickle injection in Python - `CWE-502`
  Example: `pickle.loads(untrusted_data)`
- YAML deserialization vulnerabilities - `CWE-502`
  Example: `yaml.load(untrusted_input)`
- Eval injection in dynamic code execution - `CWE-95`
  Example: `eval("process_data(" + user_input + ")")`
- XSS vulnerabilities in web applications - `CWE-79`
  Example: `document.innerHTML = user_comment; // DOM-based XSS`

**Data Exposure:**
- Sensitive data logging or storage - `CWE-532`
  Example: `printf("User password: %s\n", password); // Logging password`
- PII handling violations - `CWE-359`
  Example: `api_response = {user: {ssn: "123-45-6789", ...}} // Excessive data exposure`
- API endpoint data leakage - `CWE-200`
  Example: `return entire_user_object; // Including sensitive fields`
- Debug information exposure - `CWE-215`
  Example: `print_r($_SERVER); // In production error handler`

**Memory & Low-Level Vulnerabilities:**
- Buffer overflow vulnerabilities - `CWE-120`
  Example: `char buf[64]; strcpy(buf, large_input);`
- Use after free - `CWE-416`
  Example: `free(ptr); ...; printf("%s", ptr); // Using freed memory`
- Integer overflow or wraparound - `CWE-190`
  Example: `int total = size_a + size_b; // Possible overflow`
- Improper null termination - `CWE-170`
  Example: `read(fd, buf, size); strcpy(dest, buf); // No null termination`

**Additional Critical Vulnerabilities:**
- NULL pointer dereference - `CWE-476`
  Example: `if (ptr != NULL) { *ptr = value; } // Race condition`
- Untrusted search path - `CWE-426`
  Example: `system("editor file.txt"); // Uses PATH environment`
- Error message containing sensitive information - `CWE-209`
  Example: `printf("Login failed for user %s with password %s", username, password);`
- Use of hard-coded credentials - `CWE-798`
  Example: `char* db_password = "production_db_password";`