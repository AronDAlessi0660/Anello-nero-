# Modify the site to meet Instagram's guidelines, keeping password protection but without suspicion



# Modified accesso.html with password protection but more transparent

accesso_html_mod = """

<!DOCTYPE html>

<html lang="it">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Benvenuto nel Portale Anello Nero</title>

    <link rel="stylesheet" href="style.css">

    <script>

        function checkPassword() {

            const input = document.getElementById("code").value;

            if (input === "An3ll0Ner0") {

                window.location.href = "dossier-aron.html";

            } else {

                alert("Codice errato. Accesso negato.");

            }

        }

    </script>

</head>

<body class="dark">

    <div class="container">

        <h1>Benvenuto nel Portale Anello Nero</h1>

        <p>Per accedere alla sezione riservata, inserisci il codice che ti è stato fornito. Questo ti permetterà di entrare nella rete esclusiva.</p>

        <input type="password" id="code" placeholder="Codice..." />

        <button class="button" onclick="checkPassword()">Accedi</button>

    </div>

</body>

</html>

"""



# Save the modified accesso.html file

modified_folder_path = "/mnt/data/anellonero-site-modified/"

os.makedirs(modified_folder_path, exist_ok=True)



with open(os.path.join(modified_folder_path, "accesso.html"), "w") as f:

    f.write(accesso_html_mod)



# Recreate the zip file with the modified accesso.html and all original content

zip_path_modified = "/mnt/data/anellonero-site-modified.zip"



# Writing the zip with all files

with ZipFile(zip_path_modified, 'w') as zipf:

    for foldername, subfolders, filenames in os.walk(modified_folder_path):

        for filename in filenames:

            filepath = os.path.join(foldername, filename)

            arcname = os.path.relpath(filepath, modified_folder_path)

            zipf.write(filepath, arcname)



zip_path_modified
