# Poznawanie i eksplorowanie
## [Wprowadzenie do wdrażania systemów operacyjnych](understand/introduction-to-operating-system-deployment.md)
## [Kroki sekwencji zadań](understand/task-sequence-steps.md)
## [Zmienne akcji sekwencji zadań](understand/task-sequence-action-variables.md)
## [Wbudowane zmienne sekwencji zadań](understand/task-sequence-built-in-variables.md)
## [Polecenia przeduruchomieniowe dla nośnika sekwencji zadań](understand/prestart-commands-for-task-sequence-media.md)

# Planowanie i projektowanie
## [Wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](plan-design/infrastructure-requirements-for-operating-system-deployment.md)
## [Uwagi dotyczące planowania automatyzacji zadań](plan-design/planning-considerations-for-automating-tasks.md)
## [Bezpieczeństwo i ochrona prywatności przy wdrażaniu systemów operacyjnych](plan-design/security-and-privacy-for-operating-system-deployment.md)
## [Planowanie współdziałania wdrożenia systemu operacyjnego](plan-design/planning-for-operating-system-deployment-interoperability.md)

# Wprowadzenie
## [Przygotowanie roli systemu lokacji do wdrażania systemów operacyjnych](get-started/prepare-site-system-roles-for-operating-system-deployments.md)
## [Przygotowywanie do wdrożenia systemu operacyjnego](get-started/prepare-for-operating-system-deployment.md)
### [Zarządzanie obrazami rozruchowymi](get-started/manage-boot-images.md)
#### [Dostosowywanie obrazów rozruchowych](get-started/customize-boot-images.md)

### [Zarządzanie obrazami systemu operacyjnego](get-started/manage-operating-system-images.md)
#### [Dostosowanie obrazów systemu operacyjnego](get-started/customize-operating-system-images.md)

### [Zarządzanie pakietami uaktualnień systemu operacyjnego](get-started/manage-operating-system-upgrade-packages.md)
### [Zarządzanie sterownikami](get-started/manage-drivers.md)
### [Zarządzanie stanem użytkownika](get-started/manage-user-state.md)
### [Przygotowywanie do wdrażania nieznanych komputerów](get-started/prepare-for-unknown-computer-deployments.md)
### [Tworzenie skojarzeń użytkowników z komputerem docelowym](get-started/associate-users-with-a-destination-computer.md)

## [Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE w celu zredukowania ruchu w sieci WAN](get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md)

# Wdrażanie i użytkowanie
## [Scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw](deploy-use/scenarios-to-deploy-enterprise-operating-systems.md)
### [Uaktualnianie systemu Windows do najnowszej wersji](deploy-use/upgrade-windows-to-the-latest-version.md)
### [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)
### [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](deploy-use/install-new-windows-version-new-computer-bare-metal.md)
### [Zastępowanie istniejącego komputera i transferowanie ustawień](deploy-use/replace-an-existing-computer-and-transfer-settings.md)

## [Metody wdrażania systemów operacyjnych dla przedsiębiorstw](deploy-use/methods-to-deploy-enterprise-operating-systems.md)
### [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE](deploy-use/use-pxe-to-deploy-windows-over-the-network.md)
### [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center](deploy-use/use-software-center-to-deploy-windows-over-the-network.md)
### [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego](deploy-use/use-bootable-media-to-deploy-windows-over-the-network.md)
### [Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci](deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network.md)
### [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu multiemisji](deploy-use/use-multicast-to-deploy-windows-over-the-network.md)
### [Tworzenie obrazu dla producenta OEM w fabryce lub lokalnym magazynie](deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)
### [Wdrażanie funkcji Windows to Go](deploy-use/deploy-windows-to-go.md)

## [Zarządzanie systemem Windows jako usługą](deploy-use/manage-windows-as-a-service.md)
## [Monitorowanie wdrożeń systemów operacyjnych](deploy-use/monitor-operating-system-deployments.md)
## [Tworzenie wdrożenia fazowego dla sekwencji zadań](deploy-use/create-phased-deployment-for-task-sequence.md)

## [Zarządzanie sekwencjami zadań do automatyzacji zadań](deploy-use/manage-task-sequences-to-automate-tasks.md)
### [Tworzenie sekwencji zadań instalacji systemu operacyjnego](deploy-use/create-a-task-sequence-to-install-an-operating-system.md)
### [Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego](deploy-use/create-a-task-sequence-to-upgrade-an-operating-system.md)
### [Tworzenie sekwencji zadań w celu przechwycenia systemu operacyjnego](deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)
### [Tworzenie sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika](deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)
### [Zarządzanie wirtualnymi dyskami twardymi za pomocą sekwencji zadań](deploy-use/use-a-task-sequence-to-manage-virtual-hard-disks.md)

## [Niestandardowe scenariusze sekwencji zadań](deploy-use/custom-task-sequence-scenarios.md)
### [Tworzenie niestandardowej sekwencji zadań](deploy-use/create-a-custom-task-sequence.md)
### [Tworzenie sekwencji zadań dla wdrożeń innych niż wdrożenia systemów operacyjnych](deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)
### [Kroki sekwencji zadań w celu zarządzania przejściem z systemu BIOS na interfejs UEFI](deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion.md)
### [Wstępna aprowizacja funkcji BitLocker w systemie Windows PE](deploy-use/preprovision-bitlocker-in-windows-pe.md)

## [Tworzenie nośnika sekwencji zadań](deploy-use/create-task-sequence-media.md)
### [Tworzenie nośnika samodzielnego](deploy-use/create-stand-alone-media.md)
### [Tworzenie wstępnie przygotowanego nośnika](deploy-use/create-prestaged-media.md)
### [Tworzenie nośnika rozruchowego](deploy-use/create-bootable-media.md)
### [Tworzenie nośnika przechwytywania](deploy-use/create-capture-media.md)
