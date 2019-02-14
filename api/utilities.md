# Utilities

The API also includes a number of utility functions to help you in your plugin development.

## toggleShowNodeId

Toggle showing node ID's in the layers panel.

```javascript
figmaPlus.toggleShowNodeId();
```

## isDesktop

Checks if Figma is running on the Desktop app. Returns a `boolean`.

```javascript
figmaPlus.isDesktop();
```

## getFileKey

Get the current opened file's unique key.

```javascript
figmaPlus.getFileKey();
```

## getOrgs

Get an array of Orgs related to your account.

```javascript
figmaPlus.getOrgs();
```

## getMyOrgId

Get the ID of your current Org.

```javascript
figmaPlus.getMyOrgId();
```

## getTeams

Get an array of teams related to your account.

```javascript
figmaPlus.getTeams();
```

## getMyTeams

Get an array of teams you are in.

```javascript
figmaPlus.getMyTeams();
```
