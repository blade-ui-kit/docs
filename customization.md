# Customization

Blade UI Kit was designed to put you, the developer, in control. We often deep customization, overwriting component classes and views. This guide was put together to guide you through the process of manipulating things to your taste.

**An important note before you proceed** is that if you don't really need customization but rather just want to set defaults, we recommend to use composition over publishing. [Read more about composition with Blade UI Kit here](/docs/{version}/introduction#composition).

## Overwriting Components

One type of customization is overwriting components. You publish both a component's class and view with the following command:

```bash
php artisan buk:publish color-picker
```

Or use the `--class` & `--view` as described below.

In general it's important to note that if you take this approach you need to **be sensible about the things you adjust**. You can't simple rename properties and methods and expect everything to still work. Write tests for your new components and don't wander too far from the defaults.

### Overwriting Classes

You can customize component's by overwriting their classes. To start off with publishing a component's class you can use the `buk:publish` command and the `--class` flag:

```bash
php artisan buk:publish color-picker --class
```

Running this command will create a new class for you as `app/View/Components/Forms/Inputs/ColorPicker.php` which mimics the directory structure in Blade UI Kit. It will also publish the `blade-ui-kit.php` config file if you haven't published it yet and replace the Blade UI Kit component with yours in it. Just like that.

This allows you to immediately get started with overwriting the component. Add & overwrite methods, set defaults, etc.

> One thing to note is that the `$assets` property is a reserved property within Blade UI Kit components.

### Overwriting Views

You can also publish the view of a component. Run the `buk:publish` command and the `--view` flag for this:

```bash
php artisan buk:publish color-picker --view
```

Running this command will publish the component's view to `resources/view/vendor/blade-ui-kit/components/forms/inputs/color-picker.blade.php`. In here you'll have a copied view of the original view file. You don't need to overwrite the class if you just want to adjust the view as the component's class will automatically pick up on the newly published view.

## Copying Components

Of course, if customizing isn't your thing, or even using the library as a dependency, nothing stops you from copying the components directly into your app. You're definitely free to do this but we can't guarantee support if you do so. 

Also some credit if you copy code somewhere (prefereable the readme of the repository) is always appreciated.
