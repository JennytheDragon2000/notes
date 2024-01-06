![[attach/202401061905.png]]


![[attach/202401061932.png]]

When we make a commit, each commit gets this weird looking hash, this long series of numbers and letters
that is supposed to be unique that corresponds to the contents of a commit.
Plus a couple of other things.
If you don't know about hashing functions, don't worry.
You don't need to understand any of it in order to use git.
I'd say most people don't who still use Git daily.
I will have a video in sort of an appendix at the end of the course or towards the end.
That goes into some more details about how the hashing actually works.
What is hash together, what hashing algorithm is used?
It's called SHA one.
Anyway, all that we need to know is that every commit has this unique hash, this unique identifier
that corresponds to the commits, and each commit references.
At least one parent commit that came before it.
So here we can see this most recent commit in blue has a commit that came before it, right?
This pink one and before that came this purply blue one.
![[attach/202401061933.png]]

And that happens to be the initial commit.
It does not have anything before it.
It does not have a parent commit.
That happens the very first time you commit.
So we have this linear history where one commit leads to the next, which leads to the next.
But often when we're working on a real project in the real world, we need to work in multiple contexts
simultaneously.
So imagine I'm working, I don't know, I work at some company, I'm working on a web application and
I'm trying out two different color scheme variations for a website.
And I want to try them both out and figure out which one I like best.
![[attach/202401061934.png]]

And at the same time, I also have been tasked with trying to fix a really horrible bug.
But this bug is proving very difficult to solve.
I'm actually needing to delete some code and comment stuff out, move stuff around to try and hunt down
the bug.
So it's not as simple as just fixing a typo.
I have to like totally destroy part of the code base to find this bug.
And at the same time, one of my teammates is working on adding a new feature, a little chat bot and
the bottom corner.
You know, those things that pop up and you can chat with customer service or something.
It's not clear at the moment if our company wants to use that, but he's going ahead and trying it as
a bit of an experiment.
And then another coworker is adding some new functionality to the search bar autocomplete, and yet
another developer is doing something very different.
She is doing a very experimental radical design overhaul of our entire application layout, but it won't
be presented until next month and we don't even know if any of it will be used after next month.
So lots of different contexts.
If we all worked in a linear fashion, one commit after the next, this would be practically impossible.
How could we be working on separate things, some of which break other people's code?
Right.
If I'm trying to fix a horrible bug and deleting a bunch of code, removing files, I'm just making
a mess.
That's going to be a big problem if somebody else is trying to add a new feature.
Likewise, if someone is doing a radical experimental design change on every single view of our application,
everything changes.
But I'm trying to work on some minor color scheme variations, or if someone's working on adding a chat
widget to the bottom right of our screen.
Those things need to happen in separate contexts because they have implications on one another and they
really need to happen in isolation until maybe at some point we decide to incorporate changes into each
other's contexts.
So that is where branching comes in.
That's exactly what git branches allow us to do.
![[attach/202401061935.png]]

Branches are a signature feature of Git and you can kind of think of them as alternative timelines for
a project.
They allow us to create separate contexts whenever we want.
We can try new things.
We can work on multiple ideas in parallel.
We can experiment, we can break stuff, and whatever we do on one branch will not impact what happens
on other branches, although we can decide to then combine branches, we call that merging and we'll
learn how to do that.
But that's something we have to decide to do.
Otherwise, if we make a change in one branch, the other branches do not know about it.
They exist in isolation.
So this allows me to make a commit and maybe make another commit on one branch and then at any point
splinter off and try something on this pink branch up top.
I'm calling New Color Scheme.
![[attach/202401061936.png]]

I could try a new color scheme out, but over here, if I switch back to this branch, none of that
code comes with me.
None of those new commits.
So I could branch off again and work on a bug fix.
![[attach/202401061936_1.png]]

But again, totally separate context.
And then I could branch off even further from this bug fix branch and branch further to do an experimental
redesign.
![[attach/202401061936_2.png]]

So now I have at least four different contexts one, two, three and four.
And this means that I could be working on this and maybe somebody else is working on this branch and
somebody else is working here or.
![[attach/202401061936_3.png]]

Maybe someone else is working on this purply bluish branch in the middle and working on things plotting
ahead.
Well, I'm still stuck here.
We're all working in separate contexts, but then a very important part is being able to then combine
and merge branches together when appropriate.
If you work on a bug fix and you actually solve it, then you want to merge that bug fix into the main
code base or into another branch.
So we'll learn how to do all of this in time.
![[attach/202401061937.png]]

So even though we haven't really used the term branch, we haven't made branches or referenced themin any way.![[attach/202401061952_1.png]]

In Git you are always working on a branch and we've seen evidence of this.You've hopefully seen this before.![[attach/202401061953.png]]

On Branch Master, nothing to commit or it may not say nothing to commit, but on branch master something.So in any repository, here's my first novel if I type git status.![[attach/202401061953_1.png]]

Here we are on Branch Master and you can see the way I have my terminal configured.It also shows me my branch that I'm on currently.It shows master here.That's what that is.So when we learn how to change branches, you'll see that updated as well on this right hand side.So we're always on a branch.Even though we didn't decide to be on the master branch, we didn't create the master branch.It's just there for us.And that's exactly what the master branch is.It's just the default branch name.When you make a new git repository, when we run Git in it, automatically the branch that we starton is called Master.![[attach/202401061953_2.png]]

Now it doesn't do anything special, it doesn't have any fancy powers whatsoever.It's just like any other branch, every single possible branch you create, they have the same abilities,the same commands.There's nothing special about Master except for the fact that it just happens to be made for you.Now, some people do treat the master branch as special in their own project.![[attach/202401061954.png]]

They treat it as the source of truth, the official project branch, the main branch where they don'twant to mess anything up.So they treat the master branches like our official working code base.And then I'll try things on other branches and if they work I combine them back into master.But again, that is a choice that you make or that specific developers make.From gets perspective, the master branch is just like any other branch.It does not have to hold the master copy of your project.You can delete it, you can rename it.And in fact, I want to talk about renaming it for a moment.![[attach/202401061956.png]]

This is a topic that will come up again a couple of times throughout the course.The name on Git and GitHub for the default branch name for a long time was Master.However, in 2020, GitHub announced that they were renaming the default branch name from master toMain as part of a larger push by tech companies to try and avoid any potentially offensive language.So GitHub, again, just GitHub made this change from master to main with Git.However, what we're using, we haven't touched GitHub yet.Git, the default branch name is still master and that's why we see things like on Branch Master.We didn't name it master, it's just the default branch name.However, there are conversations happening and that may change in the future.And I will also show you how to change the default branch name.If you want to do this, it's easy to do, but I'm going to wait until we talk a little bit more aboutbranches.I don't want to talk about renaming and changing branch names before we even really understand whatthey are.So we will come back to this.But I want to bring this up because on most of the documentation, tutorials, videos that you see outthere, you will see the term master branch as the default branch name and over time more and more peoplewill likely adopt main.So we'll put a pin in that for now and my slides are going to continue to use Master just because itis what your get is going to show you.![[attach/202401061957.png]]

Branch Master.But once we get to GitHub, we will use Main OC.So I mentioned that there's nothing special at all about the master branch, but a lot of companiesare.A lot of people treat it as your main branch where things should always be working.It should be the main copy of your code base or of your project.![[attach/202401061957_1.png]]

![[attach/202401061957_2.png]]

So you could then make a branch to try something experimental and make some commits and test somethingout.![[attach/202401061957_3.png]]

And then if you like that you can incorporate it back to Master Branch or you can abandon it and justmove on and keep working on your master branch and just not incorporate this experimental branch.![[attach/202401061958.png]]

This is an approach a lot of people use.It's a very common workflow and we will actually have a section on git workflows and collaboration patterns.But this is a very, very common one.It's called feature branching or creating feature branches.So you have your main or your master branch which acts as the source of truth, and then you add newfeature branches and merge them back in when it makes sense.So here's another version of the same thing.![[attach/202401061958_1.png]]

Well, we have Ethyl and Fitz working on their own branches, and then our master branch or the mainbranch where their changes can be merged in.But for us at the moment, the only significance of the master branch is that it just exists.So next we're going to learn how to make our own branches and how to switch between them.But before that, we're actually going to talk about this right here.![[attach/202401061958_2.png]]

So there's one more concept we need to get out of the way before we can talk about creating branches,which is this thing right here.Head You've probably seen this before.When we type git log, for example, every commit shows up.Hopefully that's review.![[attach/202401062004.png]]

And in our case we see the most recent commit the top one, this thing head arrow master.So what exactly is that thing?![[attach/202401062005.png]]

Head in all caps.What does it mean?Well, it's just a term in git.Specifically, it is a pointer that refers to our current location in the repository and it points to![[attach/202401062005_1.png]]

a particular branch reference.So there's some terminology in there, branch reference we have not discussed.So I'm going to break it down here.I like to think of branches as bookmarks.In a book.![[attach/202401062005_2.png]]

We can have a whole bunch of different bookmarks, different places in a book.So let's say this is where I left off in the book and this is where I'm sharing it with my friend.This is where Fitz left off and this is where Ethel left off in the book.Three different spots.At any given point in time, only one of those spots can be open.Right.We can't have the book open to multiple pages.So only one is active.Only one is being read or being viewed.It's actually open to that bookmark.So that is what head refers to.![[attach/202401062017.png]]

Head is our current location that we are viewing or that we are checking out is a common term you'llhear.So in our case, we haven't done anything with head, we haven't made any branches.![[attach/202401062018.png]]

So Head always is referring to our master branch, the last commit on our master branch.And that's what we see here.![[attach/202401062018_1.png]]

Everything's on our master branch.Head refers to master.That's what this arrow means.Head pointing to the master branch.And this is all master branch.This is what we call the tip of the branch.It's the last commit, the most recent one.So head refers to the branch pointer.I know it's crazy terminology.Then if I had more branches, if I switch to a different branch like I switched to Ethel's branch head![[attach/202401062018_2.png]]

points to the tip of Ethel Branch, or I take a look at Fitz's branch.I've switched there.![[attach/202401062018_3.png]]

This is what I have open in our massive book.This is the thing I currently have active in my repository.Head points there.I believe the term originates from a play head I think is what it's called on an old tape machine ortape recorder.I don't know.![[attach/202401062018_4.png]]

I'm out of my depth here, but it had some analogue meaning in the real world.So one more diagram to make this clear.It probably won't make it clear just yet, but more practice will.I want to reiterate, head is a pointer.![[attach/202401062019.png]]

It's a reference to a branch pointer and a branch pointer is where a branch currently is.It's like that bookmark in a book we can have a whole bunch of branches and each one has a branch referencethat just refers to where that branch is.![[attach/202401062019_1.png]]

So let me demonstrate this.We started on our master branch.That's where we are now.And every project we've done, we're on master head points to master.I do some more work, I make a commit, I'm still on master.![[attach/202401062019_2.png]]

So this branch pointer updates to my new commit and head stays the same.It's still master, but then I decide I want to try something experimental.I'm going to make a new branch, so I want to try adding a dark mode to my website so I make a new branch.We'll learn how to do that soon.Dark Mode still refers to the same commit as master.They are at the same point, right?![[attach/202401062020.png]]

They are two branch references pointing at the same thing and head points to dark mode, which meansI'm on the dark mode branch.So now if I make a new commit, I do some new work.Things diverge.Master stays where it was.![[attach/202401062020_1.png]]

It's pointing to this commit but dark mode now has a new commit.It refers to and head still points to dark mode.So if I do new work, I'm on dark mode.That's the branch I currently am on.So that new commit is on dark mode.![[attach/202401062020_2.png]]

This dark mode pointer updates to this commit instead of that one.And then I can switch back at any point I could go back to master.Remember, I think of it as a bookmark in a book, so we still have that bookmark.That's what this reference is, and I can open to that page by switching over to this branch.![[attach/202401062020_3.png]]

Head is pointing to master and I could go back to dark mode go back to master head is just the thingthat is currently open that I'm currently checking out in my repository so we can have hundreds of thesedifferent branches.Each branch has a branch reference pointing to where we left off.That's really the key takeaway here.A branch is just a reference to some commit and as we make more commits, even if we're just on themaster branch, I make a new commit.That master pointer now reflects that change it updates to point to that new commit.So over here originally when this was the only commit master was pointing to this commit and then tothis commit and then to this commit.And now it's all the way up to this commit here.They're all in the master branch.This is the tip of the master branch here.And then at any point we can create different branches and splinter off into different directions.You can have all these different branch pointers referring to different commits and then switch betweenthem by moving ahead.All right.![[attach/202401062021.png]]

Okey dokey. It's time to learn our first command.That has to do with branching.And it's pretty simple.One, it is get branch, get space branch, nothing else.This will just give us a list of our current existing branches in a repo so it doesn't make a new branch,it doesn't switch branches, it just shows you the current branches.In our case, we haven't made new branches, so we won't see anything except Master.So I'm on my first novel for now.![[attach/202401062028.png]]

I'm going to make a new repository in a moment.![[attach/202401062029.png]]

If I type git branch, I see one branch master and to get out of here, just like with git log I typeq.Now I'll show you a different project.![[attach/202401062029_1.png]]

This repository has a couple more branches.If I type git branch, you can see them all here.Birds.![[attach/202401062029_2.png]]

Birds of prey.California mammals.Hawks.Mammals.Master no animals.Owls.Stash test.I was testing something out there.You can see though, there's a bunch of branches, but the one that is active has a little asterisk![[attach/202401062056.png]]

next to it.![[attach/202401062056_1.png]]

All right.So next up, we're going to learn how to make our first branch.![[attach/202401062057.png]]

And we actually use the same command that we just saw get branch, except now we add on a branch name.So get branch with a branch name, we'll create a branch with that name versus Git branch without anythingelse.![[attach/202401062058.png]]

Just lists the current branches.So get branch branch name and your branch name.We'll talk a little bit more about later, but it shouldn't include spaces.Let's just start with that.And generally you want it to make sense and be informative, but you don't need to write a whole sentenceto explain what the branch is.Also, this simply makes a branch for us.It does not switch to the branch.![[attach/202401062058_1.png]]

So I'm on my master branch here.As you can see, head points at master.![[attach/202401062058_2.png]]

I have two commits on the master branch when I run this command to get branch bug fix.That makes me a new branch called Bug Fix.It's based off of the head where I currently was, so it points to the same exact spot.But I have a new branch.I have not switched to it.I'm still on, master.So I'll demonstrate this to you.Let's make a new branch.But first, I'm actually going to work on a separate project, a separate repo.Instead of working on the novel.![[attach/202401062058_3.png]]

We were writing The Great Gatsby.I'm going to make a new repo.I'm in a folder.I'm just calling it branching and I'm going to make a directory.I'm going to make a road trip playlist folder.So often when I'm teaching this stuff, I'm torn if I should do something.Very easy to follow along with.Something simple to understand.Or if I should do something realistic, I'm going to try and do both.But I'm going to start with the super simple, easy to understand project.So it's not really a project.We're going on a road trip and I want a playlist of songs and I'm going to use Git for whatever reasonto track those songs and I'll make some different branches.So I'm going to start by making my repository.![[attach/202401062059.png]]

So I'm in a folder, road trip playlist.I'm going to run, get it.So I have an empty repo.![[attach/202401062059_1.png]]

I know that I wasn't in a git repo, but I should have checked to see with git status.But I know that I wasn't.And then I'm going to go ahead and make a file.I'm going to call it playlist.![[attach/202401062059_2.png]]

Dot txt and I'll open this up in my editor.So here it is.I'm just going to start by adding a very simple heading like song artist.So it's just the header heading for the playlist.All right, I'm going to add that file, get add playlist, get commit.![[attach/202401062100.png]]

I'm on the master branch, of course, just by default.Add playlist header.All right, we type get log.![[attach/202401062100_1.png]]

All right.So next up, we're going to learn how to make our first branch.And we actually use the same command that we just saw get branch, except now we add on a branch name.So get branch with a branch name, we'll create a branch with that name versus Git branch without anythingelse.Just lists the current branches.So get branch branch name and your branch name.We'll talk a little bit more about later, but it shouldn't include spaces.Let's just start with that.And generally you want it to make sense and be informative, but you don't need to write a whole sentenceto explain what the branch is.Also, this simply makes a branch for us.It does not switch to the branch.So I'm on my master branch here.As you can see, head points at master.I have two commits on the master branch when I run this command to get branch bug fix.That makes me a new branch called Bug Fix.It's based off of the head where I currently was, so it points to the same exact spot.But I have a new branch.I have not switched to it.I'm still on, master.So I'll demonstrate this to you.Let's make a new branch.But first, I'm actually going to work on a separate project, a separate repo.Instead of working on the novel.We were writing The Great Gatsby.I'm going to make a new repo.I'm in a folder.I'm just calling it branching and I'm going to make a directory.I'm going to make a road trip playlist folder.So often when I'm teaching this stuff, I'm torn if I should do something.Very easy to follow along with.Something simple to understand.Or if I should do something realistic, I'm going to try and do both.But I'm going to start with the super simple, easy to understand project.So it's not really a project.We're going on a road trip and I want a playlist of songs and I'm going to use Git for whatever reasonto track those songs and I'll make some different branches.So I'm going to start by making my repository.So I'm in a folder, road trip playlist.I'm going to run, get it.So I have an empty repo.I know that I wasn't in a git repo, but I should have checked to see with git status.But I know that I wasn't.And then I'm going to go ahead and make a file.I'm going to call it playlist.Dot txt and I'll open this up in my editor.So here it is.I'm just going to start by adding a very simple heading like song artist.So it's just the header heading for the playlist.All right, I'm going to add that file, get add playlist, get commit.I'm on the master branch, of course, just by default.Add playlist header.![[attach/202401062102.png]]

All right, we type get log.![[attach/202401062102_1.png]]

We see head is pointing to the master branch.Now I'm going to add two songs just to add songs to start that I happen to like.There they are songs.Great song, one of us also great song.I'm going to add those.I just want to have one or two commits on my master branch.So I'm going to do git add playlist, get commit, add to Abi's songs.All righty.![[attach/202401062103.png]]

So I'm on the master branch, right?Head points to master.We have two commits.Now let's make a new branch.For whatever reason I decide I want to make a different playlist based on this one that only containsoldies.So maybe I'm not sure what I want on my main playlist, so I'm going to try a couple of options, andthat's exactly what I'm going to do, is make some different branches and I'm going to make a branchcalled oldies, and it's just going to include songs that are they're not technically what the radiowould classify as oldies, but let's just say anything from before, like 2000, which I recognize formost people is not oldies.So to make a branch, get branch and then a branch name.So let's make that oldest branch get branch, I'll make this full screen.And then actually before I do that, let's just do Git Branch.We're on master.It's the only branch now if I do get branch oldies.And hit enter.Hmm.It doesn't seem like anything happened.I'm still on, Master.If I type get status, I'm still on master.No surprise there.It doesn't switch us over.But if I type get branch, we do see we have a new branch oldies.We're just not on it.Head is still pointing to master.You can see that again type get log head is pointing to master.But now we have this new reference oldies.It's at the same commit right to branch references pointing to the same thing.We just happen to be on master.So we're at this stage two branches.![[attach/202401062107.png]]

They're both referring to the same point, the same commit and we're on master.So to switch branches, there's a command that we can use called get switch.![[attach/202401062108.png]]

So this is actually a newer command in Git.I'll do a separate video on the older command.We used something called Git Checkout to do the same thing.We'll talk about that.It's still used in other contexts, but get switch was introduced to switch between branches, so getswitch and then a branch name.![[attach/202401062108_1.png]]

So in our example here, if I do get switch bug fix head is now pointing to that bug fix branch.It was on master, now it's on bug fix.So in our case we have this oldest branch, we are not on it.![[attach/202401062108_2.png]]

We see that we're on master type get status, we're on master.But if I do get switch oldies and I do need to spell it correctly so if I reference something that doesn't![[attach/202401062109.png]]

exist, it tells me there's no branch with that name.But if I do get switch oldies.Hey switch to branch oldies.My terminal shows oldies over here.![[attach/202401062109_1.png]]

![[attach/202401062109_2.png]]

If I type get status on branch oldies and if I type git log you can now see head is pointing to oldies.Still the same commit though I haven't done any new work.However, if I do some new work and make a new commit here, this is the oldies playlist.So what should we add?Let's add to good great George Jones songs.He stopped loving her today.Great song.Great song.![[attach/202401062110.png]]

So I'm going to save and I'm going to commit now when I commit here, remember, I'm on the Old EastBranch, so get add playlist, get commit, add to George Jones songs just like that.And we just made our first commit on a new branch.![[attach/202401062111.png]]

![[attach/202401062111_1.png]]

We're on the oldest branch and if I type get log, we're going to see something we haven't yet seen.We see head referring to oldies.That's what we expect to see.It's our most recent commit.That's where oldest is because we're on the oldest branch.But we see Master now has been left behind on this previous commit.Master is still remember this idea of a bookmark in the book.![[attach/202401062111_2.png]]

It's still bookmarking this commit.This is master, this is oldies and we happen to be on the oldest branch.But I can switch as we've seen with git switch.So if I switch right now this is what we have on our oldest branch.![[attach/202401062112.png]]

If I switch over, get switch to master.Take a look.![[attach/202401062112_1.png]]

Now we have just two lines, just two songs, rather.We don't have the George Jones stuff that we did.If I type, get log on the master branch.![[attach/202401062112_2.png]]

We only have these two commits, add the playlist header, add two ABBA songs, but when I switch back,get switch to oldies.![[attach/202401062113.png]]

We now have our two George Jones songs in addition and I type get log, we have that extra commit.So that was just our first example of making a branch and switching.We will get more practice in the next video, but just to remind you, get branch on its own, we'lllist branches, get branch with a branch name, makes a branch and then to switch to a branch we use![[attach/202401062113_1.png]]

