Upload these files to the ROOT of your GitHub repository and replace the old files.

Included:
- index.html
- manifest.json
- README_UPLOAD_FIRST.txt

What was fixed:
- Preserved the billing-code dataset from your uploaded HTML
- Kept the code-search logic for both code number and procedure name
- Inserted your Supabase project URL and publishable key
- Added a defensive check if the Supabase library fails to load

After uploading:
1. Commit and push to GitHub
2. Wait for GitHub Pages to redeploy
3. Open the live site in an incognito/private tab
4. Hard refresh if needed

If clicking "Envoyer le code" still fails after this, the next likely issue is in Supabase settings:
- Email template
- URL Configuration
- RLS/table setup in SQL
