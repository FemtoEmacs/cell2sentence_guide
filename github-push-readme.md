# How to git push

Change the remote to SSH:

`git remote set-url origin git@github.com:FemtoEmacs/cell2sequence_guide.git`

Now verify:

`git remote -v'

You should see:

```
origin  git@github.com:FemtoEmacs/cell2sequence_guide.git (fetch)
origin  git@github.com:FemtoEmacs/cell2sequence_guide.git (push)
```

Run:

```
ssh -T git@github.com
```

Commit:


~/cell2sentence_guide$ git add .
~/cell2sentence_guide$ git commit -m "React to cell2sentence."
~/cell2sentence_guide$ git push
