Tree-View Componente for svelete based on Bootstrap 5

![TreeView](/tree.png?raw=true "TreeView")

## Prerequiste
For this component you need Bootstrap 5. You can add the files in <svelte:head>

```html
<svelte:head>
	<link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.min.css">
	<link rel="stylesheet" href="node_modules/bootstrap-icons/font/bootstrap-icons.css">
</svelte:head>
```

## Usage

```js
<script>
  import Tree from './treeComponent/Tree.svelte';

  let root = [
		{
			title: 'Important work stuff',
			disabled: true,
			children: [
				{ title: 'quarterly-results.xlsx' }
			]
		},
		{
			title: 'Animal GIFs',
			children: [
				{
					title: 'Dogs',
					expanded: true,
					children: [
						{ title: 'treadmill.gif' },
						{ title: 'rope-jumping.gif' }
					]
				},
				{
					title: 'Goats',
					children: [
						{ title: 'parkour.gif' , visible:false},
						{ title: 'rampage.gif' }
					]
				},
				{ title: 'cat-roomba.gif' },
				{ title: 'duck-shuffle.gif' },
				{ title: 'monkey-on-a-pig.gif' }
			]
		},
		{ title: 'TODO.md' }
	];

let config = {
		icons:{
			expanded: 'bi bi-folder2-open',
			folder: 'bi bi-folder2',
			document: 'bi bi-file-earmark',
			disabled: 'bi bi-folder-x'
		}
	};

let dblClick = function(event){
	alert('Clicked' + event.detail.title);
}

</script>

<svelte:head>
	<link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.min.css">
	<link rel="stylesheet" href="node_modules/bootstrap-icons/font/bootstrap-icons.css">
</svelte:head>

<main>
  <h1>Hello world!</h1>

  <Tree title="Home" treeData={root} expanded visible={true} treeConfig={config} on:treeNodeDoubleClick={dblClick}/>
 
</main>

<style>
 
</style>
```

## Props of Tree-Component

| value | description |
|---|---|
| title | title of the root node |
| treeData | JSON data for the tree |
| expanded | is the node expanded by default |
| treeConfig | config Object |
| visible | is the node visible - if you dont want a root node you can use this prop |
| on:treeNodeDoubleClick | event handler for double click [in progress] |


## Node Data

| value | description |
|---|---|
| title | title of the node |
| disabled | is the node disabled - a disabled node can not be expanded |
| expanded | is the node expanded by default |
| visible | is the node visible - if you dont want a root node you can use this prop |

## Config Object

The confing Object can be used to change the default icons. The values are the css-class.
```js
{
  icons:{
    expanded: 'bi bi-folder2-open',
    folder: 'bi bi-folder2',
    document: 'bi bi-file-earmark',
    disabled: 'bi bi-folder-x'
  }
}
```
