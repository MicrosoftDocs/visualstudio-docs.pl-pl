---
title: Wykrywanie wymagań systemowych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788473"
---
# <a name="detecting-system-requirements"></a>Wykrywanie wymagań systemowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage nie może działać, jeśli program Visual Studio nie jest zainstalowany. W przypadku zarządzania instalacją pakietu VSPackage przy użyciu programu Microsoft Instalator Windows można skonfigurować Instalatora w celu wykrycia, czy program Visual Studio jest zainstalowany. Można ją również skonfigurować do sprawdzania systemu pod kątem innych wymagań, na przykład konkretnej wersji systemu Windows lub określonej ilości pamięci RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Wykrywanie wersji programu Visual Studio  
 Aby określić, czy jest zainstalowana wersja programu Visual Studio, sprawdź, czy w odpowiednim folderze znajduje się wartość "Install Registry Key" (REG_DWORD) 1, zgodnie z opisem w poniższej tabeli. Należy pamiętać, że istnieje hierarchia wersji programu Visual Studio:  
  
1. Enterprise  
  
2. Professional Edition  
  
3. Społeczność  
  
   Po zainstalowaniu wersji "wyższej" są dodawane klucze rejestru dla tej wersji, jak również w przypadku wersji "Lower". Oznacza to, że jeśli jest zainstalowana wersja Enterprise, klucz instalacji jest ustawiony na 1 dla przedsiębiorstwa, a także dla wersji Professional i Community. W związku z tym należy tylko sprawdzić, czy jest wymagana wersja najwyższej wersji.  
  
> [!NOTE]
> W 64-bitowej wersji edytora rejestru, klucze 32-bitowe są wyświetlane w obszarze HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node \\ . Klucze programu Visual Studio są objęte HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing \\ .  
  
|Produkt|Klucz|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Powłoka programu Visual Studio 2015 (Zintegrowana i izolowana)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Wykrywanie, gdy program Visual Studio jest uruchomiony  
 Nie można prawidłowo zarejestrować pakietu VSPackage, jeśli program Visual Studio jest uruchomiony po zainstalowaniu pakietu VSPackage. Instalator musi wykryć, kiedy program Visual Studio jest uruchomiony, a następnie odmówić zainstalowania programu. Instalator Windows nie umożliwia korzystania z wpisów tabeli w celu włączenia takiego wykrywania. Zamiast tego należy utworzyć akcję niestandardową w następujący sposób: należy użyć `EnumProcesses` funkcji, aby wykryć proces devenv.exe, a następnie ustawić właściwość Instalatora, która jest używana w warunku uruchamiania, lub warunkowo wyświetlić okno dialogowe, które wyświetla użytkownikowi komunikat o zamknięciu programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
