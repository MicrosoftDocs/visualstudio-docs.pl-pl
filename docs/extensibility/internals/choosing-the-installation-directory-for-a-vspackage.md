---
title: Wybieranie katalogu instalacyjnego dla pakietu VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a5016c528e754e452ee1248e85b705c41a44ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621074"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Wybieranie katalogu instalacyjnego dla pakietu VSPackage
Pakietu VSPackage i towarzyszące mu pliki muszą znajdować się w systemie plików użytkownika. Lokalizacja zależy od tego, czy pakietu VSPackage odbywa się lub niezarządzane schematu przechowywania wersji side-by-side i wybór użytkownika.

## <a name="unmanaged-vspackages"></a>Niezarządzane pakietów VSPackage
 Niezarządzane pakietu VSPackage jest serwera COM, który można zainstalować w dowolnym miejscu. Swoje informacje rejestracyjne musi dokładnie odzwierciedlać jego lokalizacji. Instalator interfejsu użytkownika (UI) należy podać lokalizację domyślną jak podkatalog `ProgramFilesFolder` wartość właściwości Instalatora Windows. Na przykład:

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*

 Użytkownik powinien może zmienić domyślny katalog, aby dopasować użytkowników, którzy nadal partycją rozruchową małych i preferowanie tych instalacji aplikacji i narzędzi na innym woluminie.

 Jeśli schemat side-by-side używa określonej wersji pakietu VSPackage, można użyć podkatalogów przechowywać różne wersje. Na przykład:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Managed VSPackages
 Zarządzane pakietów VSPackage można również zainstalować w dowolnym miejscu. Jednak należy rozważyć, zawsze instalowania ich do globalnej pamięci podręcznej zestawów (GAC), aby skrócić czas ładowania zestawu. Ponieważ pakietów VSPackage zarządzane są zawsze zestawy o silnych nazwach, instalowania ich w pamięci podręcznej GAC oznacza, że ich weryfikacji podpisu silnej nazwy przyjmuje tylko w czasie instalacji. Zestawy o silnych nazwach, zainstalowany w innym miejscu w systemie plików musi mieć ich podpisy zweryfikowane za każdym razem, gdy są one załadowane. Po zainstalowaniu pakietów VSPackage zarządzanych w pamięci podręcznej GAC Użyj narzędzie regpkg **/Assembly** przełącznika na zapisywanie wpisów rejestru, wskazując silnej nazwy zestawu.

 Po zainstalowaniu pakietów VSPackage zarządzanych w lokalizacji innej niż pamięci podręcznej GAC, postępuj zgodnie z wcześniej przekazanej niezarządzanych pakietów VSPackage dotyczące wybierania hierarchie katalogów. Użyj narzędzia regpkg **/ codebase** przełącznika na zapisywanie wpisów rejestru wskazuje ścieżkę zestawu pakietu VSPackage.

 Aby uzyskać więcej informacji, zobacz [rejestrowanie i wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelitarne biblioteki dll
 Zgodnie z Konwencją pakietu VSPackage satelitarne biblioteki dll, które zawierają zasoby dla danego ustawienia regionalnego, znajdują się w podkatalogach *pakietu VSPackage* katalogu. Podkatalogi odpowiadają wartościom identyfikator ustawień regionalnych.

 [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md) artykułu wskazuje, że wpisy rejestru kontrolują lokalizację [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] faktycznie szuka pakietu VSPackage satelickiej biblioteki DLL. Jednak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować satelitarnej biblioteki DLL w podkatalogu o nazwie wartości identyfikatora LCID, w następującej kolejności:

1.  Domyślny identyfikator LCID (LCID usługi Visual Studio, na przykład *\1033* w języku angielskim)

2.  Domyślnie LCID podjęzyk domyślne.

3.  Ustawienia domyślne systemu LCID.

4.  Ustawienia domyślne systemu LCID z odmianą języka domyślnego.

5.  Federalna Angielski (*. \1033* lub *. \0x409*).


Jeśli biblioteka DLL pakietu VSPackage zawiera zasoby i **SatelliteDll\DllName** punkty wejścia rejestru, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować je w podanej kolejności.

## <a name="see-also"></a>Zobacz także
- [Wybieranie między udostępnionymi i wersjonowanymi pakietami VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Manage VSPackages](../../extensibility/managing-vspackages.md)
- [Zarządzanie rejestracją pakietu](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)