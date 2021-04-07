---
title: Podręcznik użytkowania programu Visual Studio w przedsiębiorstwie
description: Konfigurowanie i rozwiązywanie problemów z programem Visual Studio w środowisku przedsiębiorstwa.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e5e8a28ac89c2bea85aee8323060bf948266ad2e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547391"
---
# <a name="visual-studio-enterprise-guide"></a>Podręcznik użytkowania programu Visual Studio w przedsiębiorstwie
Jeśli chcesz zaoszczędzić czas podczas korzystania z firmy w programie Visual Studio, Zacznij tutaj. Ten przewodnik po przedsiębiorstwie zawiera wskazówki, które mogą pomóc w instalacji i aktualizacji programu Visual Studio w typowych scenariuszach dla przedsiębiorstw, uzyskać odblokowywanie w przypadku wystąpienia problemów i dowiedzieć się, jak zgłosić problem, jeśli potrzebujesz więcej pomocy. 

## <a name="get-started"></a>Rozpoczęcie pracy 
Dowiedz się, jak wdrożyć program Visual Studio w przedsiębiorstwie w środowiskach sieciowych i w trybie offline.

- **[Włączanie aktualizacji administratorów przy użyciu programu Microsoft Endpoint Configuration Manager (SCCM)](enabling-administrator-updates.md)**.  Aktualizacje programu Visual Studio znajdują się w [wykazie Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) i [Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus). Administratorzy przedsiębiorstwa mogą następnie pobrać aktualizację i rozesłać ją do maszyn klienckich programu Visual Studio w całej organizacji przy użyciu standardowych narzędzi do wdrażania, takich jak Microsoft Endpoint Configuration Manager (SCCM).

- Informacje **o opcjach wdrażania w przedsiębiorstwie w środowiskach sieciowych**. [Przewodnik administratora programu Visual Studio](visual-studio-administrator-guide.md) zawiera wskazówki oparte na scenariuszu dla administratorów systemu. 

- **[Uzyskaj porady dotyczące rozwiązywania problemów](troubleshooting-installation-issues.md)**. Uzyskaj pomoc podczas instalowania lub aktualizowania programu Visual Studio i Dowiedz się, jak zgłosić problem, jeśli jest zablokowany. Te porady zawierają instrukcje krok po kroku, które powinny rozwiązać większość problemów z instalacją w trybie online lub offline. 

- **[Utwórz instalację w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)**. Jeśli nie masz połączenia z Internetem lub nie masz ograniczonej łączności z Internetem, Znajdź opcje instalacji programu Visual Studio. 

- **[Utwórz pakiety programu inicjującego](../deployment/creating-bootstrapper-packages.md)**. Dowiedz się, jak utworzyć niestandardowe pakiety programu inicjującego, tworząc manifesty produktów i pakietów. 

- **[Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)**. Możesz programowo zastosować swój klucz produktu w ramach skryptu, który służy do automatyzowania wdrożenia programu Visual Studio. Można programowo ustawić klucz produktu na urządzeniu w trakcie instalacji programu Visual Studio lub po zakończeniu instalacji. 

## <a name="install-visual-studio"></a>Instalowanie programu Visual Studio 

Dowiedz się, jak zainstalować program Visual Studio w popularnych scenariuszach dla przedsiębiorstw. 

- **[Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md)**. Użyj różnych parametrów, aby kontrolować lub dostosowywać instalację programu Visual Studio. Automatyzuj proces instalacji lub Utwórz pamięć podręczną plików instalacyjnych do późniejszego użycia. Aby uzyskać więcej informacji, zobacz [przykłady parametrów wiersza polecenia](command-line-parameter-examples.md).

- **[Utwórz instalację sieciową programu Visual Studio](create-a-network-installation-of-visual-studio.md)**. Buforowanie plików dla początkowej instalacji wraz ze wszystkimi aktualizacjami produktów w jednym folderze. 

- **[Instaluj i używaj programu Visual Studio i usług platformy Azure za zaporą lub serwerem proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)**. Jeśli w organizacji używane są miary zabezpieczeń, takie jak zapora lub serwer proxy, istnieją adresy URL domeny, które można dodać do "dozwolonych" i portów i protokołów, które mogą być otwierane w celu uzyskania najlepszego środowiska podczas instalowania i używania usług Visual Studio i Azure. 

- **[Zainstaluj wymagane certyfikaty do instalacji w trybie offline](../install/install-certificates-for-visual-studio-offline.md)**. Zainstaluj wymagane certyfikaty, jeśli komputer kliencki jest całkowicie odłączony od Internetu.

## <a name="update-visual-studio"></a>Aktualizowanie programu Visual Studio 

Dowiedz się, jak pomyślnie zaktualizować program Visual Studio i rozwiązać problemy z aktualizacją. 

- **[Zastosuj aktualizacje administratorów przy użyciu programu Microsoft Endpoint Configuration Manager (SCCM)](../install/applying-administrator-updates.md)**. Dowiedz się więcej na temat dystrybuowania aktualizacji funkcji, zabezpieczeń i jakości programu Visual Studio za poorednictwem oprogramowania SCCM. 

- **[Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)**. Zaktualizuj układ instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, aby można było go użyć zarówno jako punktu instalacji, jak i dla najnowszej aktualizacji programu Visual Studio, a także aby zachować instalacje, które są już wdrożone na stacjach roboczych klienta.

- **[Zaktualizuj program Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)**. Zapoznaj się z wartością w obszarze Aktualizacja dla linii bazowej i popoznaj się z różnicą między wersjami pomocniczymi i aktualizacjami obsługi. 

- **[Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline](update-minimal-layout.md)**. W przypadku komputerów, które nie są połączone z Internetem, tworzenie minimalnego układu jest najłatwiejszym i najszybszym sposobem na aktualizację wystąpień programu Visual Studio w trybie offline.

- **[Napraw program Visual Studio](repair-visual-studio.md) , aby rozwiązać problemy z aktualizacją**. Czasami instalacja programu Visual Studio przestała być uszkodzona lub uszkodzona. Naprawa jest przydatna w przypadku rozwiązywania problemów dotyczących czasu instalacji we wszystkich operacjach instalacji, w tym aktualizacji. 

- **Obserwuj [linie bazowe zabezpieczeń systemu Windows](/windows/security/threat-protection/windows-security-baselines)**. Firma Microsoft jest przeznaczona dla klientów z bezpiecznymi systemami operacyjnymi, takimi jak Windows 10 i Windows Server, oraz zabezpieczonymi aplikacjami, takimi jak Microsoft Edge. Oprócz zapewnienia bezpieczeństwa swoich produktów firma Microsoft umożliwia również precyzyjne sterowanie środowiskami, zapewniając różne możliwości konfiguracji. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też 

- [Przewodnik dotyczący produktywności dla programu Visual Studio](../ide/productivity-features.md)

