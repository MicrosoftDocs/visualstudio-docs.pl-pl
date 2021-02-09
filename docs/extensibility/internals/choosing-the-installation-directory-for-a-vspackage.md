---
title: Wybieranie katalogu instalacyjnego dla pakietu VSPackage | Microsoft Docs
description: Dowiedz się, jak wybrać katalog instalacji dla pakietu VSPackage i plików pomocniczych, używając takich czynników, jak, czy są zarządzane lub niezarządzane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea697e6e445eeae117bb6bf1d1603220ec0c0675
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874077"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Wybierz katalog instalacji dla elementu pakietu VSPackage
Pakietu VSPackage i jego pliki pomocnicze muszą znajdować się w systemie plików użytkownika. Lokalizacja zależy od tego, czy pakietu VSPackage jest zarządzany, czy niezarządzany, schemat obsługi wersji równoległej i wybór użytkownika.

## <a name="unmanaged-vspackages"></a>Niezarządzany pakietów VSPackage
 Niezarządzany pakietu VSPackage to serwer COM, który można zainstalować w dowolnej lokalizacji. Informacje o rejestracji muszą dokładnie odzwierciedlać jego lokalizację. Interfejs użytkownika Instalatora (UI) powinien podać domyślną lokalizację jako podkatalog `ProgramFilesFolder` wartości właściwości Instalator Windows. Na przykład:

*&lt;Folderprogramfiles &gt; \\ &lt; &gt; \\ &lt; MyVSPackageProduct &gt; \V1.0\\*

 Użytkownik powinien mieć możliwość zmiany domyślnego katalogu w celu uwzględnienia użytkowników, którzy przechowują małą partycję rozruchową i woli instalować aplikacje i narzędzia na innym woluminie.

 Jeśli schemat równoległy używa wersji pakietu VSPackage, można użyć podkatalogów do przechowywania różnych wersji. Na przykład:

 *&lt;Folderprogramfiles &gt; \\ &lt; &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2002\\*

 *&lt;Folderprogramfiles &gt; \\ &lt; &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2003\\*

 *&lt;Folderprogramfiles &gt; \\ &lt; &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>Zarządzane pakietów VSPackage
 Zarządzane pakietów VSPackage można również zainstalować w dowolnej lokalizacji. Należy jednak wziąć pod uwagę, że należy je zawsze zainstalować w globalnej pamięci podręcznej zestawów (GAC), aby skrócić czas ładowania zestawu. Ponieważ zarządzane pakietów VSPackage są zawsze zestawami o silnej nazwie, instalowanie ich w pamięci podręcznej oznacza, że ich weryfikacja podpisu o silnej nazwie odbywa się tylko w czasie instalacji. Zestawy o silnych nazwach zainstalowane w innym miejscu w systemie plików muszą mieć zweryfikowane podpisy przy każdym załadowaniu. Instalując zarządzane pakietów VSPackage w pamięci podręcznej GAC, należy użyć przełącznika **/Assembly** narzędzia RegPkg, aby zapisać wpisy rejestru wskazujące silną nazwę zestawu.

 W przypadku instalowania pakietów VSPackage zarządzanych w lokalizacji innej niż pamięć podręczna, należy postępować zgodnie z wcześniejszymi wskazówkami dotyczącymi niezarządzanych pakietów VSPackage w celu wybrania hierarchii katalogów. Użyj przełącznika **/codebase** narzędzia RegPkg, aby zapisać wpisy rejestru wskazujące ścieżkę zestawu pakietu VSPackage.

 Aby uzyskać więcej informacji, zobacz [register and Unregister pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Biblioteki DLL Satellite
 Zgodnie z Konwencją pakietu VSPackage satelitarne biblioteki DLL, które zawierają zasoby dla konkretnych ustawień regionalnych, znajdują się w podkatalogach katalogu *pakietu VSPackage* . Podkatalogi odpowiadają wartościom identyfikatora ustawień regionalnych (LCID).

 Artykuł [Zarządzaj pakietów VSPackage](../../extensibility/managing-vspackages.md) wskazuje, że wpisy rejestru określają, gdzie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rzeczywiście szukamy satelitarnej biblioteki dll pakietu VSPackage. Jednak program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podejmie próbę załadowania satelickiej biblioteki DLL w podkatalogu o nazwie dla wartości LCID w następującej kolejności:

1. Domyślny identyfikator LCID (identyfikator LCID programu Visual Studio, na przykład *\ 1033* dla języka angielskiego)

2. Domyślny identyfikator LCID z domyślnym językiem.

3. Domyślny identyfikator LCID systemu.

4. Domyślny identyfikator LCID systemu z domyślnym językiem.

5. Angielski (*. \ 1033* lub *.\0x409*).

Jeśli biblioteka DLL pakietu VSPackage zawiera zasoby i wskazuje na nią wpis rejestru **SatelliteDll\DllName** , program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podejmie próbę załadowania ich w powyższej kolejności.

## <a name="see-also"></a>Zobacz też
- [Wybierz między udostępnionym i z wersją pakietów VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)
- [Zarządzanie rejestracją pakietów](/previous-versions/bb166783(v=vs.100))