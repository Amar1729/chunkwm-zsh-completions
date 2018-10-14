
# Zsh Completions for chunkwm

Completions for the tiling WM for macOS, [chunkwm](https://github.com/koekeishiya/chunkwm). Chunkwm is still in active development, so some of these completions may still be updated.

These completions will be bundled with the chunkwm brew formulae, so you should only need to install this plugin if you build chunkwm manually or if you want to update them independently of chunkwm.

## Note for Chunkwm Plugin Authors

You can create your own completions if desired by bootstrapping of off `_chunkc`:

```bash
# Fake chunkc plugin

function _chunkc_plugin_set {
    # your own completions here
    return
}

function _chunkc_plugin_get {
    # your own completions here
    return
}

function _chunkc_plugin {
    local context state state_descr line
    typeset -A opt_args

    _arguments -C \
        "1:my new plugin:_sep_parts '(plugin)' :: '(set get)'"

    # allows _chunkc to be called initially, but not once "plugin::*" is completed
    # _chunkc will call any function in this file following the naming syntax:
    # _chunc_plugin_*
    if [[ ${line[1]} != "plugin::"* ]]; then
        _chunkc
    fi
}
```

## Standard Installation for a Zsh Plugin

### Oh-My-ZSH
With [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) installed:

```bash
git clone https://github.com/Amar1729/chunkwm-zsh-completions ~/.oh-my-zsh/custom/plugins/chunkwm-zsh-completions
echo "plugins+=(chunkwm-zsh-completions)" >> ~/.zshrc
```

### Antigen
Add `antigen bundle Amar1729/chunkwm-zsh-completions` to your `.zshrc` wherever you're adding the other antigen bundles.
