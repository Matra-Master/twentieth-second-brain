---
created: 20230801-1648
tags:
  - Resources/talk
  - Resources/docker
  - Resources/wsl
---

# Prerequisitos

- Windows 10 >= 21H2, o Windows 11 >= 21H2
- WSL 2 feature on Windows [Microsoft documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
* Una distro de linux instalada en el WSL2. Recomendable [Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV?hl=es-ar&gl=ar&rtc=1)

## Turn on Docker Desktop WSL 2

1. Navigate to **Settings**.
2. From the **General** tab, select **Use WSL 2 based engine**..

## Enabling Docker support in WSL 2 distros

Check WSL mode:

    wsl.exe -l -v

Set Version: 

    wsl.exe --set-version ubuntu 2


Opcional: Setear la distro por defecto de WSL

    wsl --set-default <distro name>


## Develop with Docker and WSL 2

* Instalar extensión [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)



---
## Related Ideas

* [[Docker]]

## Sources
[Docker documentation](https://docs.docker.com/desktop/wsl/)
