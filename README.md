# projecttest

## To Run

### Install Node LTS

First ensure you are on the latest version of Node. An easy way to do this is to use [nvm](https://github.com/nvm-sh/nvm/blob/master/README.md)

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
nvm --version //checks to see if the installation was successful
nvm install --lts //installs latest LTS version
nvm use --lts
```

### Install Global Dependecies

```
yarn global add nx
```

### Install Pods - Mac

```
sudo gem install cocoapods
sudo gem install cocoapods-bugsnag
```

### Clone and Install Repo

```
git clone git@github.com:miviewintegratedsolutions/MiView.git
cd MiView
yarn
```

If you see the message "There appears to be trouble with your network connection. Retrying..." you may need to increase the network timeout:

```
yarn install --network-timeout=60000
```

### Run MiView - PC

```
yarn start MiView
```

### Run MiTrade - Mac

#### Terminal 1

```
yarn start MiTrade
```

#### Terminal 2

```
yarn mitrade:pods
```

#### Xcode

Open Xcode and open the workspace file under `./apps/MiTrade/ios/MiTrade.xcworkspace`.

Go to Copy Bundle Resources and add all files under `Resources`. Also, add `GoogleMaps.Bundle`.

Choose your simulator and click Play.

#### Issues you might run into

If you run into an error related to no `main.jsbundle` not being located, run

```
yarn bundle MiTrade
```

If the error persists, in the project navigator tab, right click on the MiTrade folder. If the main.jsbundle is in red, right click and delete the reference. Then, click "Add Files to...". Navigate to the ios folder and select "main.jsbundle". Make sure the first checkbox is checked under "Add to targets". Click "Add".

If you run into node runtime errors in the simulator, try running this before the previous steps

```
yarn clearCache
```

### Run MiDia - Mac

#### Terminal 1

```
yarn start MiDia
```

#### Terminal 2

```
yarn midia:pods
```

#### Xcode

Open Xcode and open the workspace file under `./apps/MiDia/ios/MiDia.xcworkspace`.

Choose your simulator and click Play.

#### Issues you might run into

If you run into an error related to no `main.jsbundle` not being located, run

```
yarn bundle MiDia
```

If the error persists, in the project navigator tab, right click on the MiDia folder. If the main.jsbundle is in red, right click and delete the reference. Then, click "Add Files to...". Navigate to the ios folder and select "main.jsbundle". Make sure the first checkbox is checked under "Add to targets". Click "Add".

If you run into node runtime errors in the simulator, try running this before the previous steps

```
yarn clearCache
```

## To Deploy (WIP)

### IOS apps

1. Open the tablet app workspace file in Xcode.

(MiTrade Only) - Go to Copy Bundle Resources and remove all icon assets. Also, remove `GoogleMaps.Bundle`. When archiving, these copies are considered duplicate resources.

2. Click `Product > Archive`.

If you run into this error while archiving:

```
main.jsbundle does not exist. This must be a bug with + echo 'React Native
```

Go to Xcode. In the project navigator tab, right click on the MiDia/MiTrade folder. Click "Add Files to...". Navigate to the ios folder and select "main.jsbundle". Make sure the first checkbox is checked under "Add to targets". Click "Add" and try to archive again.
