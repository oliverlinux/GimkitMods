<script lang="ts">
    import Menu from "./Menu.svelte";
    import Group from "./Group.svelte";
    import ColorPicker from "./components/ColorPicker.svelte";
    
    import { showHud } from '../stores';
    import keybindManager from "../keybindManager";
    import ResetStyles from "./ResetStyles.svelte" ;
    
    import CosmeticPicker from "../scripts/customization/CosmeticPicker.svelte";
    import CustomTheme from "../scripts/customization/customTheme/CustomTheme.svelte";


    keybindManager.addKeybind(new Set(["\\"]), () => {
        showHud.update(v => !v);
    })
</script>

<div id="gc-hud" style="display: {$showHud ? 'block' : 'none'}">
    <Menu name="Customization">
        <Group name="HUD Appearance">
            <ColorPicker text="Text Color" bindValue="textColor" minOpactiy={0.3} />
            <Group name="Menu Appearance">
                <ColorPicker text="Background Color" bindValue="menuBackgroundColor" />
                <ColorPicker text="Outline Color" bindValue="menuOutlineColor" />
                <ColorPicker text="Header Color" bindValue="menuHeaderBackgroundColor" />
                <ColorPicker text="Header Text Color" bindValue="menuHeaderTextColor" />
            </Group>
            <Group name="Button Appearance">
                <ColorPicker text="Background Color" bindValue="buttonBackgroundColor" />
                <ColorPicker text="Outline Color" bindValue="buttonBorderColor" />
            </Group>
        </Group>
        <ResetStyles />
        <CosmeticPicker />
        <CustomTheme />
    </Menu>


</div>

<style>
#gc-hud {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 9999999999;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    color: var(--textColor);
}
</style>
