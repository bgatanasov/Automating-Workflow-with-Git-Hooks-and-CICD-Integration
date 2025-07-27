pre-commit HOOK code!

#!/bin/sh

echo " Prettier is runnig to check ..."

npx prettier . --check

if [ $? -ne 0 ]; then
echo "Prettier foun error and stopped!"
exit 1
fi

echo "Prettier pass all and conitnue with commit!"
