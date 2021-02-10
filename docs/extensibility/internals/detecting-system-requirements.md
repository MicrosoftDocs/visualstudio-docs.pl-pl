---
title: Wykrywanie wymagań systemowych | Microsoft Docs
description: Dowiedz się, jak skonfigurować Instalator Windows firmy Microsoft w celu wykrywania wymagań systemowych, takich jak zainstalowana wersja programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20287ba123c5736c9eb7077622623f4a739bde5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963474"
---
# <a name="detect-system-requirements"></a>Wykrywanie wymagań systemowych
Pakietu VSPackage nie może działać, jeśli program Visual Studio nie jest zainstalowany. W przypadku zarządzania instalacją pakietu VSPackage przy użyciu programu Microsoft Instalator Windows można skonfigurować Instalatora w celu wykrycia, czy program Visual Studio jest zainstalowany. Można ją również skonfigurować do sprawdzania systemu pod kątem innych wymagań, na przykład konkretnej wersji systemu Windows lub określonej ilości pamięci RAM.

## <a name="detect-visual-studio-editions"></a>Wykryj wersje programu Visual Studio
 Aby określić, czy jest zainstalowana wersja programu Visual Studio, sprawdź, czy w odpowiednim folderze znajduje się wartość " **Install** Registry Key" *(REG_DWORD) 1* , zgodnie z opisem w poniższej tabeli. Należy pamiętać, że istnieje hierarchia wersji programu Visual Studio:

1. Przedsiębiorstwa

2. Professional Edition

3. Społeczność

Gdy jest zainstalowana nowsza wersja, klucze rejestru dla tej wersji są dodawane oraz dla wcześniejszych wersji. Oznacza to, że jeśli jest zainstalowana wersja Enterprise, klucz **instalacji** jest ustawiony na *1* dla przedsiębiorstwa, a także dla wersji Professional i Community. W związku z tym należy sprawdzić tylko najnowszą wymaganą wersję.

> [!NOTE]
> W 64-bitowej wersji edytora rejestru, w obszarze **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\** są wyświetlane klucze 32-bitowe. Klucze programu Visual Studio są objęte **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produkt|Klucz|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Powłoka programu Visual Studio 2015 (Zintegrowana i izolowana)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Wykryj, kiedy program Visual Studio jest uruchomiony
 Nie można prawidłowo zarejestrować pakietu VSPackage, jeśli program Visual Studio jest uruchomiony po zainstalowaniu pakietu VSPackage. Instalator musi wykryć, kiedy program Visual Studio jest uruchomiony, a następnie odmówić zainstalowania programu. Instalator Windows nie umożliwia korzystania z wpisów tabeli w celu włączenia takiego wykrywania. Zamiast tego należy utworzyć akcję niestandardową w następujący sposób: należy użyć `EnumProcesses` funkcji, aby wykryć proces *devenv.exe* , a następnie ustawić właściwość Instalatora, która jest używana w warunku uruchamiania, lub warunkowo wyświetlić okno dialogowe, które wyświetla użytkownikowi komunikat o zamknięciu programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
