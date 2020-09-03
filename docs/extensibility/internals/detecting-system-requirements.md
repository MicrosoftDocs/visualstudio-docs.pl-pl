---
title: Wykrywanie wymagań systemowych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708735"
---
# <a name="detect-system-requirements"></a>Wykrywanie wymagań systemowych
Pakietu VSPackage nie może działać, jeśli program Visual Studio nie jest zainstalowany. W przypadku zarządzania instalacją pakietu VSPackage przy użyciu programu Microsoft Instalator Windows można skonfigurować Instalatora w celu wykrycia, czy program Visual Studio jest zainstalowany. Można ją również skonfigurować do sprawdzania systemu pod kątem innych wymagań, na przykład konkretnej wersji systemu Windows lub określonej ilości pamięci RAM.

## <a name="detect-visual-studio-editions"></a>Wykryj wersje programu Visual Studio
 Aby określić, czy jest zainstalowana wersja programu Visual Studio, sprawdź, czy w odpowiednim folderze znajduje się wartość " **Install** Registry Key" *(REG_DWORD) 1* , zgodnie z opisem w poniższej tabeli. Należy pamiętać, że istnieje hierarchia wersji programu Visual Studio:

1. Enterprise

2. Professional Edition

3. Społeczność

Gdy jest zainstalowana nowsza wersja, klucze rejestru dla tej wersji są dodawane oraz dla wcześniejszych wersji. Oznacza to, że jeśli jest zainstalowana wersja Enterprise, klucz **instalacji** jest ustawiony na *1* dla przedsiębiorstwa, a także dla wersji Professional i Community. W związku z tym należy sprawdzić tylko najnowszą wymaganą wersję.

> [!NOTE]
> W 64-bitowej wersji edytora rejestru, klucze 32-bitowe są wyświetlane w obszarze **HKEY_LOCAL_MACHINE \software\wow6432node \\ **. Klucze programu Visual Studio są objęte **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\devdiv\vs\servicing \\ **.

|Produkt|Klucz|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Powłoka programu Visual Studio 2015 (Zintegrowana i izolowana)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Wykryj, kiedy program Visual Studio jest uruchomiony
 Nie można prawidłowo zarejestrować pakietu VSPackage, jeśli program Visual Studio jest uruchomiony po zainstalowaniu pakietu VSPackage. Instalator musi wykryć, kiedy program Visual Studio jest uruchomiony, a następnie odmówić zainstalowania programu. Instalator Windows nie umożliwia korzystania z wpisów tabeli w celu włączenia takiego wykrywania. Zamiast tego należy utworzyć akcję niestandardową w następujący sposób: należy użyć `EnumProcesses` funkcji, aby wykryć proces *devenv.exe* , a następnie ustawić właściwość Instalatora, która jest używana w warunku uruchamiania, lub warunkowo wyświetlić okno dialogowe, które wyświetla użytkownikowi komunikat o zamknięciu programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
