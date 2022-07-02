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
