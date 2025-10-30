---
title: "Google Cloud Virtual Machine for Nightscout"
description: "Step-by-step instructions to create a free-tier Google Cloud virtual machine optimized for hosting Nightscout safely and efficiently."
layout: GCNS
---
  
# Google Cloud Virtual Machine  
[Google Cloud Nightscout](./GoogleCloud.md) >> Virtual Machine  
   
In this guide, we will create a free virtual machine in our [Google project](./NS_GCProject.md).  Each Google account is eligible for one free virtual machine.  
For additional assistance, a video clip on this page may be helpful. This process takes around 5 minutes.  
<br/>  
  
---
  
### ⚠️ WARNING!  
This virtual machine is strictly for hosting Nightscout. Do not use it for work, banking, trading, shopping, or development.   
<br/>  
  
---  
  
Go to [Google Cloud](https://cloud.google.com/).  
Sign in.  
Click on "Console".  
Click on "Activate Cloud Shell" at the top right to the left of the Notification (bell) symbol.  
Authorize Cloud Shell.  
  
Copy the following script and paste into the Cloud Shell terminal and enter.  
<br/>  
  
<div style="position: relative">
  <button onclick="copyScript()" style="border: 1px solid #0066ff; color:#f0f0f0; background: linear-gradient(#0066ff, #0066ff); font-size:14px; background-color:#0066ff; font-weight:400; border-radius: 2px; margin-left:70px; margin-top:8px; padding:4px 12px; display:inline-block; box-shadow: inset 0px 1px 0px rgba(255,255,255,.3), 0px 1px 5px rgba(0,0,0,.7); :hover ">Copy</button>
  <pre><code id="vmScript" style="border:none; color:#101010; background-color:#ededed; width:100%; font-size:15px">
#!/bin/bash
# Create a Nightscout VM with a random free-tier region
# Checks if an instance already exists before proceeding

existing_vms=$(gcloud compute instances list --format="value(name)")

if [[ -n "$existing_vms" ]]; then
  echo "⚠️  Existing virtual machines found:"
  echo "$existing_vms"
  echo
  read -p "Do you still want to create a new VM? (y/N): " confirm
  confirm=$(echo "$confirm" | tr '[:upper:]' '[:lower:]')
  if [[ "$confirm" != "y" && "$confirm" != "yes" ]]; then
    echo "Aborted. No new VM was created."
    exit 0
  fi
fi

regions=("us-west1" "us-central1" "us-east1")
region=${regions[$RANDOM % ${#regions[@]}]}
zone=$(gcloud compute zones list --filter="region:($region)" --format="value(name)" | shuf -n 1)

echo "Selected region: $region"
echo "Selected zone:   $zone"
echo

gcloud compute instances create gcns-2025-10-30 \
  --machine-type=e2-micro \
  --zone="$zone" \
  --image-project=ubuntu-os-cloud \
  --image-family=ubuntu-minimal-2404-lts-amd64 \
  --boot-disk-size=30GB \
  --boot-disk-type=pd-standard \
  --network-tier=STANDARD \
  --tags=http-server,https-server \
  --no-boot-disk-auto-delete \
  --no-shielded-secure-boot \
  --maintenance-policy=MIGRATE \
  --no-restart-on-failure \
  --provisioning-model=STANDARD \
  --no-enable-display-device
  </code></pre>
</div>

<script>
function copyScript() {
  const code = document.getElementById("vmScript").innerText;
  navigator.clipboard.writeText(code);
  alert("✅ Script copied to clipboard!");
}
</script>

  
