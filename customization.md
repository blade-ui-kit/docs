# Customization

Blade UI Kit was designed to put you, the developer, in control. We offer deep customization, overwriting component classes and views. This guide was put together to help you through the process of manipulating things to your taste.

**An important note before you proceed** is that if you don't really need customization but rather just want to set defaults, we recommend to use composition over publishing. [Read more about composition with Blade UI Kit here](/docs/{{version}}/introduction#composition).

## Overwriting Components

One type of customization is overwriting components. You can publish both a component's class and view with the following command:

```bash
php artisan buk:publish color-picker
```

Or use the `--class` & `--view` flags as described below.

In general it's important to note that if you take this approach you need to **be sensible about the things you adjust**. You can't simply rename properties and methods and expect everything to still work. Write tests for your new components and don't wander too far from the defaults. **We also don't offer any guarantee that things will keep working in future (major) versions.**

### Overwriting Classes

You can customize components by overwriting their classes. To start off with publishing a component's class you can use the `buk:publish` command and the `--class` flag:

```bash
php artisan buk:publish color-picker --class
```

Running this command will create a new class for you as `app/View/Components/Forms/Inputs/ColorPicker.php` which mimics the directory structure in Blade UI Kit. It will also publish the `blade-ui-kit.php` config file if you haven't published it yet and replace the Blade UI Kit component with yours in it.

This allows you to immediately get started with overwriting the component. Add & overwrite methods, set defaults, etc.

> The `$assets` property is a reserved property within Blade UI Kit components and shouldn't be overwritten.

### Overwriting Views

You can also publish the view of a component. Run the `buk:publish` command and the `--view` flag for this:

```bash
php artisan buk:publish color-picker --view
```

Running this command will publish the component's view to `resources/view/vendor/blade-ui-kit/components/forms/inputs/color-picker.blade.php`. In here you'll have a copied view of the original view file. You don't need to overwrite the class if you just want to adjust the view as the component's class will automatically pick up on the newly published view.

## Copying Components

Of course, if customizing isn't your thing, or even using the library as a dependency, nothing stops you from copying the components directly into your app. You're definitely free to do this *but we can't guarantee support if you do so*. 

Also some credit if you copy code somewhere (prefereable in the readme of the repository) is always appreciated.

An advantage to this approach is that you're less prone to breakages from the library itself with newer versions coming out, but you'll lose the nicety of getting bug fixes and new features.
