---
title: Wybieranie katalogu instalacyjnego dla pakietu VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697243"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Wybieranie katalogu instalacyjnego dla pakietu VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage i jego pliki pomocnicze muszą znajdować się w systemie plików użytkownika. Lokalizacja zależy od tego, czy pakietu VSPackage jest zarządzany, czy niezarządzany, schemat obsługi wersji równoległej i wybór użytkownika.  
  
## <a name="unmanaged-vspackages"></a>Niezarządzany pakietów VSPackage  
 Niezarządzany pakietu VSPackage to serwer COM, który można zainstalować w dowolnej lokalizacji. Informacje o rejestracji muszą dokładnie odzwierciedlać jego lokalizację. Interfejs użytkownika Instalatora (UI) powinien podać domyślną lokalizację jako podkatalog właściwości Folderprogramfiles Instalator Windows. Na przykład:  
  
 Folderprogramfiles MyCompany\MyVSPackageProduct\V1.0\  
  
 Użytkownik powinien mieć możliwość zmiany domyślnego katalogu w celu uwzględnienia użytkowników, którzy przechowują małą partycję rozruchową i woli instalować aplikacje i narzędzia na innym woluminie.  
  
 Jeśli schemat równoległy używa wersji pakietu VSPackage, można użyć podkatalogów do przechowywania różnych wersji. Na przykład:  
  
 Folderprogramfiles MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 Folderprogramfiles MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 Folderprogramfiles MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Zarządzane pakietów VSPackage  
 Zarządzane pakietów VSPackage można również zainstalować w dowolnej lokalizacji. Należy jednak wziąć pod uwagę, że należy je zawsze zainstalować w globalnej pamięci podręcznej zestawów (GAC), aby skrócić czas ładowania zestawu. Ponieważ zarządzane pakietów VSPackage są zawsze zestawami o silnej nazwie, instalowanie ich w pamięci podręcznej oznacza, że ich weryfikacja podpisu o silnej nazwie odbywa się tylko w czasie instalacji. Zestawy o silnych nazwach zainstalowane w innym miejscu w systemie plików muszą mieć zweryfikowane podpisy przy każdym załadowaniu. Instalując zarządzane pakietów VSPackage w pamięci podręcznej GAC, należy użyć przełącznika **/Assembly** narzędzia RegPkg, aby zapisać wpisy rejestru wskazujące silną nazwę zestawu.  
  
 W przypadku instalowania pakietów VSPackage zarządzanych w lokalizacji innej niż pamięć podręczna, należy postępować zgodnie z wcześniejszymi wskazówkami dotyczącymi niezarządzanych pakietów VSPackage w celu wybrania hierarchii katalogów. Użyj przełącznika **/codebase** narzędzia RegPkg, aby zapisać wpisy rejestru wskazujące ścieżkę zestawu pakietu VSPackage.  
  
 Aby uzyskać więcej informacji, zobacz [Rejestrowanie i Wyrejestrowywanie pakietów VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Biblioteki DLL Satellite  
 Zgodnie z Konwencją pakietu VSPackage satelitarne biblioteki DLL, które zawierają zasoby dla konkretnych ustawień regionalnych, znajdują się w podkatalogach katalogu pakietu VSPackage. Podkatalogi odpowiadają wartościom identyfikatora ustawień regionalnych (LCID).  
  
 [Zarządzanie pakietów VSPackage](../../extensibility/managing-vspackages.md) wskazuje, że wpisy rejestru [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sprawdzają, gdzie rzeczywiście szuka satelitarnej biblioteki dll pakietu VSPackage. Jednak program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podejmie próbę załadowania satelickiej biblioteki DLL w podkatalogu o nazwie dla wartości LCID w następującej kolejności:  
  
1. Domyślny identyfikator LCID (VS LCID na przykład \ 1033 dla języka angielskiego)  
  
2. Domyślny identyfikator LCID z domyślnym językiem.  
  
3. Domyślny identyfikator LCID systemu.  
  
4. Domyślny identyfikator LCID systemu z domyślnym językiem.  
  
5. Angielski (. \ 1033 lub .\0x409).  
  
   Jeśli biblioteka DLL pakietu VSPackage zawiera zasoby i wskazuje na nią wpis rejestru SatelliteDll\DllName, program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] podejmie próbę załadowania ich w powyższej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie między udostępnionym i z wersją pakietów VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Zarządzanie pakietów VSPackage](../../extensibility/managing-vspackages.md)   
 [Rejestracja pakietu zarządzanego](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
