# nimble-root

### The project root for your nimble repo

A Nimble Root is the project root for you or your dev team. Basically, you fork this root, with its "nimble" submodule, and use it to configure a dev environment suited to your team. By default, it will come with `[johnrom/nimble-wp-template](https://github.com/johnrom/nimble-wp-template)` which makes this a WordPress root directory. However, once more templates are built (such as Node, Angular, React, Symfony, Lavarel, Ghost, Drupal, Rails, Python, etc, hint hint), you can make this default to whatever template you want!

If your intention is to make your dev environment private (please do!), you'll have to duplicate this repo: [Read: Duplicating a Repository](https://help.github.com/articles/duplicating-a-repository)

Once you download, open bash, navigate to this folder, and run `./_nimble/nimble.sh localize`. From this point on, you can use the command `nimble` to control this script. Always run the nimble command from this root directory.

Once you've decided on a template at `_conf/default-template.conf`, you'll be able to run `nimble create myproject` and it will pull that template from Github and initialize it. Then, commit this root directory to a new repository and share it with your team.

When a team member receives a new project via pulling your new repo, they should be able to run `nimble init myproject`.
