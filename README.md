# devops-netology

NikulinMS


**/.terraform/*

Игнорирование всех собственных каталогов Terraform в любом вложении

*.tfstate
*.tfstate.*

Игнорирование всех файлов с расширением tfstate и содержаших в наименовании .tfstate.

crash.log
crash.*.log

Игнорирование логов крашей, основного и с любыми символами вместо *

*.tfvars
*.tfvars.json

Игнорирование любых файлов tfvars, которые могут содержатьличную информацию, все файлы с расширением .tfvars .tfvars.json

override.tf
override.tf.json
*_override.tf
*_override.tf.json

Игнорирование конкретных файлов и файлов с именем, содержащим на конце _override.tf  и  _override.tf.json

.terraformrc
terraform.rc

Игнорирование конкретных файлов конфигураций

Новая строка в ветке Main
