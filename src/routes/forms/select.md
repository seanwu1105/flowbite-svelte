---
layout: formLayout
---

<script>
import { onMount } from 'svelte';
import { Select, Table, TableDefaultRow, Breadcrumb } from '$lib/index'
import componentProps from '../props/Select.json'
let items = componentProps.props

let propHeader = ['Name', 'Type', 'Default']
let divClass='w-full relative overflow-x-auto shadow-md sm:rounded-lg'

let selectprops = {
  id : 'countries',
	name : 'country',
	label : 'Select your country',
}
let selected;
let fileuploadprops = {
  id : 'user_avatar',
	label : 'Upload file'
}
let fileuploadprops2 = {
  id : 'user_avatar',
  label : 'Upload file',
  helper : 'A profile picture is useful to confirm your are logged into your account'
}

  let crumbs = [
    {
      label:'Home',
      href:'/'
    },
    {
      label:'Forms',
      href:'/forms/'
    },
    {
      label:'Select',
      href:'/forms/select'
    }
  ]
</script>

<Breadcrumb {crumbs}/>


<h1 class="text-3xl w-full dark:text-white py-8">Select Components</h1>

<h2 class="text-2xl w-full dark:text-white py-4">Examples</h2>

<div class="rounded-xl w-full my-4 mx-auto bg-gradient-to-r bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-700 p-2 sm:p-6">
<Select {...selectprops} bind:value={selected}>
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="fr">France</option>
</Select>
</div>

```html
<script>
import { Select} from 'flowbite-svelte'

let selectprops = {
  id : 'countries',
	name : 'country',
	label : 'Select your country',
}
</script>

<Select {...selectprops} bind:value={selected}>
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="fr">France</option>
</Select>
```

<h2 class="text-2xl w-full dark:text-white py-4">Props</h2>

<p>The component has the following props, type, and default values. See <a href="/type-list" class="text-blue-600 hover:underline dark:text-blue-500">type-list page</a> for type information.</p>

<Table header={propHeader} {divClass} >
  <TableDefaultRow {items} rowState='hover' />
</Table>
