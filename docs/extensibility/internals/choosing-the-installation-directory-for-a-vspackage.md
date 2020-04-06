---
title: Wybór katalogu instalacyjnego dla pakietu VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709758"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Wybieranie katalogu instalacyjnego dla pakietu VSPackage
VsPackage i jego pliki pomocnicze muszą znajdować się w systemie plików użytkownika. Lokalizacja zależy od tego, czy VSPackage jest zarządzany lub niezarządzane, schemat wersji side-by-side i wybór użytkownika.

## <a name="unmanaged-vspackages"></a>Niezarządzane pakiety VS
 Niezarządzane VSPackage to serwer COM, który można zainstalować w dowolnej lokalizacji. Jego informacje rejestracyjne muszą dokładnie odzwierciedlać jego lokalizację. Interfejs użytkownika instalatora (UI) powinien zapewniać domyślną lokalizację `ProgramFilesFolder` jako podkatalog wartości właściwości Instalatora Windows. Przykład:

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*

 Użytkownik powinien mieć możliwość zmiany katalogu domyślnego, aby pomieścić użytkowników, którzy zachowują małą partycję rozruchową i wolą instalować aplikacje i narzędzia na innym woluminie.

 Jeśli schemat side-by-side używa wersji VSPackage, można użyć podkatalogów do przechowywania różnych wersji. Przykład:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Zarządzane pakiety VSPackages
 Zarządzane pakiety VSPackages można również zainstalować w dowolnej lokalizacji. Należy jednak rozważyć zawsze instalowanie ich w globalnej pamięci podręcznej zestawów (GAC), aby skrócić czas ładowania zestawu. Ponieważ zarządzane pakiety VSPackages są zawsze silne nazwy zestawów, instalowanie ich w pliku GAC oznacza, że ich weryfikacji podpisu silnej nazwy trwa tylko w czasie instalacji. Zestawy o silnych nazwach zainstalowane w innym miejscu w systemie plików muszą mieć swoje podpisy sprawdzane za każdym razem, gdy są ładowane. Po zainstalowaniu zarządzanych vspackages w pamięci podręcznej GAC, użyj przełącznika **/assembly** narzędzia regpkg do zapisu wpisów rejestru wskazujących silną nazwę zestawu.

 Jeśli zainstalujesz zarządzane pakiety VSPackages w lokalizacji innej niż GAC, postępuj zgodnie z wcześniejszymi poradami podanymi dla niezarządzanych pakietów VSPackages dla wybierania hierarchii katalogów. Użyj przełącznika **/codebase** narzędzia regpkg, aby zapisywać wpisy rejestru wskazujące ścieżkę zestawu VSPackage.

 Aby uzyskać więcej informacji, zobacz [Rejestrowanie i wyrejestrowanie pakietów VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Biblioteki DLL Satellite
 Zgodnie z konwencją biblioteki DLL sateli satelitarnej VSPackage, które zawierają zasoby dla określonych ustawień regionalnych, znajdują się w podkatalogach katalogu *VSPackage.* Podkatalogi odpowiadają wartościom identyfikatora ustawień regionalnych (LCID).

 [Artykuł Manage VSPackages](../../extensibility/managing-vspackages.md) wskazuje, że wpisy rejestru kontrolują, gdzie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] faktycznie szuka biblioteki DLL satelity vspackage. Jednak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować bibliotekę DLL satelity w podkatalogu o nazwie dla wartości LCID, w następującej kolejności:

1. Domyślna wartość LCID (Visual Studio LCID; na przykład *\1033* dla języka angielskiego)

2. Domyślny identyfikator LCID z domyślnym podjęzykiem.

3. Domyślny system LCID.

4. Domyślny systemowy identyfikator LCID z domyślnym podjęzykiem.

5. angielski amerykański (*.\1033* lub *.\0x409*).

Jeśli biblioteka DLL vspackage zawiera zasoby i **SatelliteDll\DllName** wpis rejestru punktów do niego, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] próbuje załadować je w powyższej kolejności.

## <a name="see-also"></a>Zobacz też
- [Wybierz między pakietami współużytkowanymi i wersjonowanymi pakietami VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zarządzanie rejestracją pakietu](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
