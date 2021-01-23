# Bash helpers
## Structure

- dotfiles - configs
- helpers - support heplers and aliases
- local alias
- enable veriants auto/manual
- builder all helpers to bundle file

## Enable All-In-One file
### Automatic enable
````bash
wget -P ~ 'https://raw.githubusercontent.com/spacecoding42/bash-helpers/master/init.sh' -O ~/init.sh && bash init.sh
````

### Manual enable
Copy `.helpers` folder to profile

````bash
# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

for script in ~/.helpers/*.sh ; do
    if [ -f $script ] ; then
        . $script
    fi
done
````


## Enable all files RAW
### Manual enable
````bash
if [ -f ~/bash_helpers/helpers/.bash_helpers.sh ]; then
	. ~/bash_helpers/helpers/.bash_helpers.sh
fi
````

OR

```bash

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

for dir in ~/bash_helpers/helpers/* ; do
    if [ -d $dir ] ; then
        for script in $dir/*.sh ; do
            if [ -f $script ] ; then
                    . $script
            fi
        done
    fi
done

for script in ~/bash_helpers/local/* ; do
        if [ -f $script ] ; then
                . $script
        fi
done
```

## Build All-In-One bundle file
````bash
bash build.sh
````

## Temporarily enable all helpers only on current session
````bash
wget -P ~ 'https://raw.githubusercontent.com/spacecoding42/bash-helpers/master/.helpers/bash_helpers_bundle.sh' -O ~/.bash_helpers_bundle && . ~/.bash_helpers_bundle && rm -f ~/.bash_helpers_bundle
````




    

