#dealing with secret
# create a secret filr
ansible-vault encrypt secret

ansible-playbook demo2.yml  --ask-vault-pass

# decrypt secret file
ansible-vault decrypt secret

#change password
ansible-vault rekey secret

#check syntax 
ansible-playbook demo3_block.yml --syntax-check