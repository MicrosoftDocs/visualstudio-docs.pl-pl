---
title: Wykrywanie wymagań systemowych | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445246"
---
# <a name="detecting-system-requirements"></a>Wykrywanie wymagań systemowych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage nie może działać, jeśli nie zainstalowano programu Visual Studio. Gdy Instalator systemu Microsoft Windows umożliwia zarządzanie instalacjami Twojego pakietu VSPackage, można skonfigurować Instalatora aby wykryć, czy jest zainstalowany program Visual Studio. Można również skonfigurować ją do sprawdzania systemu pod kątem innych wymagań, na przykład konkretnej wersji systemu Windows lub określoną ilość pamięci RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Detecting Visual Studio Editions  
 Aby ustalić, czy wersja programu Visual Studio jest zainstalowany, sprawdź wartość klucza rejestru instalacji (REG_DWORD) 1 w odpowiednim folderze, zgodnie z opisem w poniższej tabeli. Zwróć uwagę, że hierarchia wersje programu Visual Studio:  
  
1. Enterprise  
  
2. Professional Edition  
  
3. Społeczność  
  
   Po zainstalowaniu wersji "wyżej" klucze rejestru, w przypadku tej wersji, a także jak w przypadku wersji "niżej" są dodawane. Oznacza to jeśli jest zainstalowany w wersji Enterprise, klucz instalacji jest równa 1 dla przedsiębiorstw, a także wersje Professional i społeczności. W związku z tym należy sprawdzić tylko w przypadku wersji "najwyższą", których potrzebujesz.  
  
> [!NOTE]
> W 64-bitową wersję Edytora rejestru w 32-bitowe klucze są wyświetlane w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Klucze programu Visual Studio, podlegają HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Produkt|Key|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrated i isolated)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Wykrywanie, gdy program Visual Studio jest uruchomiony.  
 Nie można zarejestrować poprawnie Twojego pakietu VSPackage, jeśli program Visual Studio jest uruchomiony podczas instalowania pakietu VSPackage. Instalator musi wykryć, kiedy program Visual Studio jest uruchomiony i następnie odmówić zainstalować ten program. Instalator Windows nie pozwalają używać wpisów tabeli, aby umożliwić wykrywanie takich modyfikacji. Zamiast tego należy utworzyć akcję niestandardową, w następujący sposób: Użyj `EnumProcesses` funkcję, aby wykryć procesu devenv.exe, a następnie ustaw właściwość Instalatora, który jest używany w stanie uruchamiania lub warunkowo wyświetlane jest okno dialogowe, który monituje użytkownika o Zamknij program Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
