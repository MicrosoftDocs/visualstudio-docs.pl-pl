---
title: Wykrywanie wymagań systemowych | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708735"
---
# <a name="detect-system-requirements"></a>Wykrywanie wymagań systemowych
VsPackage nie może działać, chyba że jest zainstalowany program Visual Studio. Korzystając z Instalatora systemu Microsoft Windows do zarządzania instalacją programu VSPackage, można skonfigurować instalatora w celu wykrycia, czy program Visual Studio jest zainstalowany. Można również skonfigurować go, aby sprawdzić system pod kątem innych wymagań, na przykład określonej wersji systemu Windows lub określonej ilości pamięci RAM.

## <a name="detect-visual-studio-editions"></a>Wykrywanie wersji programu Visual Studio
 Aby ustalić, czy jest zainstalowana wersja programu Visual Studio, sprawdź, czy wartość **klucza** rejestru Install jest *(REG_DWORD) 1* w odpowiednim folderze, jak wymieniono w poniższej tabeli. Należy zauważyć, że istnieje hierarchia wersji programu Visual Studio:

1. Enterprise

2. Professional Edition

3. Społeczność

Po zainstalowaniu nowszej wersji klucze rejestru dla tej wersji są dodawane, a także dla wcześniejszych wersji. Oznacza to, że jeśli jest zainstalowana wersja Enterprise, klucz **instalacji** jest ustawiony na *1* dla przedsiębiorstw, a także dla wersji Professional i Community. Dlatego musisz sprawdzić tylko najnowszą wersję, której potrzebujesz.

> [!NOTE]
> W 64-bitowej wersji edytora rejestru klucze 32-bitowe są wyświetlane w **obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Klawisze programu Visual Studio znajdują się w **obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Product (Produkt)|Klucz|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serwis\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serwis\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\społeczność|
|Powłoka programu Visual Studio 2015 (zintegrowana i odizolowana)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Wykrywanie, kiedy program Visual Studio jest uruchomiony
 Nie można poprawnie zarejestrować programu VSPackage, jeśli program Visual Studio jest uruchomiony po zainstalowaniu programu VSPackage. Instalator musi wykryć, kiedy program Visual Studio jest uruchomiony, a następnie odmówić zainstalowania programu. Instalator Windows nie umożliwia włączania takiego wykrywania za pomocą wpisów tabeli. Zamiast tego należy utworzyć akcję niestandardową w `EnumProcesses` następujący sposób: Użyj funkcji do wykrywania procesu *devenv.exe,* a następnie ustaw właściwość instalatora, która jest używana w stanie uruchomienia lub warunkowo wyświetlić okno dialogowe, które monituje użytkownika o zamknięcie programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Instalowanie pakietów VSPackages z Instalatorem Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
