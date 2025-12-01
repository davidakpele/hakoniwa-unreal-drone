# Hakoniwa Unreal Drone

This repository provides visualization functionality for the Hakoniwa Drone Simulator as an Unreal Engine project. It uses Unreal Engine 5.6 to render the drone state based on PDU (Protocol Data Unit) information received via WebSocket.

## Setup

1.  Clone this repository. Since it uses submodules, please use the `--recursive` option.
    ```bash
    git clone --recursive <repository_url>
    ```
    If already cloned, initialize the submodules with:
    ```bash
    git submodule update --init --recursive
    ```
2.  Install Unreal Engine 5.6 or later.
3.  Open `HakoniwaDrone.uproject` with the Unreal Editor.
4.  Build and launch the project as needed.

## Available Levels

-   `AvatarWeb.umap` — The main level used when controlling the drone via the web.

## Key Blueprints

-   `BP_HakoniwaAvatar` — Blueprint representing the drone entity.
-   `BP_HakoniwaWebClient` — Blueprint handling WebSocket communication and PDU management.

These are located in the `Content/Blueprints` folder.

## Configuration

The PDU configuration is defined in `Content/Config/webavatar.json`. The Web Client reads this file to set up its message reception.

## Code Overview

In this project, `AHakoniwaWebClient` receives PDUs via WebSocket and applies the drone's position and rotation to `AHakoniwaAvatar`. `UDronePropellerComponent` rotates each propeller, visualizing the motor RPM.

PDU retrieval and communication leverage the [hakoniwa-pdu-unreal](https://github.com/davidakpele/hakoniwa-pdu-unreal) plugin. The plugin provides `UPduManager` and `UWebSocketCommunicationService` for reading/writing PDUs and managing connections.

The `Plugins/HakoniwaPdu` folder is a submodule. After cloning, run `git submodule update --init --recursive` to fetch it.

## License

This repository is released under the MIT License. See the `LICENSE` file for details.
