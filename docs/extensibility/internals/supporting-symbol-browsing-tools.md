---
title: Obsługa narzędzi Symbol-Browsing | Microsoft Docs
description: Program Visual Studio udostępnia możliwości przeglądania symboli w programie Visual Studio. Dowiedz się, w jaki sposób można rozłożyć te możliwości za pomocą bibliotek dla symboli w składnikach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d54f56ae3bc5fd5956f67400d84edfd4c8c9e55c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080570"
---
# <a name="supporting-symbol-browsing-tools"></a>Obsługa narzędzi do przeglądania symboli
**Przeglądarka obiektów**, **Widok klasy**, **przeglądarka wywołań** i **Znajdź narzędzia wyników symboli** zapewniają możliwości przeglądania symboli w programie Visual Studio. Te narzędzia wyświetlają hierarchiczne widoki drzewa symboli i pokazują relacje między symbolami w drzewie. Symbole mogą reprezentować przestrzenie nazw, obiekty, klasy, składowe klas i inne elementy języka zawarte w różnych składnikach. Składniki obejmują projekty programu Visual Studio, zewnętrzne składniki .NET Framework i biblioteki typu (. tlb). Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Biblioteki Symbol-Browsing
 Jako implementujący język można rozciągnąć możliwości przeglądania symboli programu Visual Studio, tworząc biblioteki, które śledzą symbole w składnikach i dostarczają listę symboli do Menedżera obiektów programu Visual Studio za pomocą zestawu interfejsów. Biblioteka jest opisana przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfejs. Menedżer obiektów programu Visual Studio reaguje na żądania nowych danych z narzędzi do przeglądania symboli, uzyskując dane z bibliotek i organizując je. Następnie wypełnia i aktualizuje narzędzia przy użyciu żądanych danych. Aby uzyskać odwołanie do Menedżera obiektów programu Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Identyfikator usługi do `GetService` metody.

 Każda biblioteka musi być zarejestrowana w Menedżerze obiektów programu Visual Studio, który gromadzi informacje we wszystkich bibliotekach. Aby zarejestrować bibliotekę, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodę. W zależności od tego, które narzędzie inicjuje żądanie, Menedżer obiektów programu Visual Studio znajduje odpowiednią bibliotekę i żąda danych. Dane przesyłane między bibliotekami i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menedżerem obiektów znajdują się na liście symboli opisanych przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejs.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Menedżer obiektów jest odpowiedzialny za okresowe odświeżanie narzędzi do przeglądania symboli w celu odzwierciedlenia najbardziej aktualnych danych zawartych w bibliotekach.

 Poniższy diagram zawiera przykład kluczowych elementów procesu żądania/wymiany danych między biblioteką i menedżerem obiektów programu Visual Studio. Interfejsy na diagramie są częścią aplikacji kodu zarządzanego.

 ![Przepływ danych między biblioteką a menedżerem obiektów](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Aby udostępnić listę symboli do Menedżera obiektów programu Visual Studio, należy najpierw zarejestrować bibliotekę w Menedżerze obiektów Visual Studio, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodę. Po zarejestrowaniu biblioteki Menedżer obiektów programu Visual Studio żąda pewnych informacji o możliwościach biblioteki. Na przykład żąda flag biblioteki i obsługiwanych kategorii przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metod i. W pewnym momencie, gdy jeden z narzędzi żąda danych z tej biblioteki, Menedżer obiektów żąda listy symboli najwyższego poziomu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metodę. W odpowiedzi Biblioteka tworzy listę symboli i udostępnia ją menedżerowi obiektów programu Visual Studio za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfejsu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Menedżer obiektów określa, ile elementów znajduje się na liście, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metodę. Wszystkie poniższe żądania odnoszą się do danego elementu na liście i podają numer indeksu elementu w każdym żądaniu. Menedżer obiektów programu Visual Studio będzie kontynuował zbieranie informacji o typie, dostępności i innych właściwościach elementu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metody.

 Określa nazwę elementu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metody i żąda informacji o ikonie przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona jest wyświetlana po lewej stronie nazwy elementu i przedstawia typ elementu, ułatwienia dostępu i inne właściwości.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Menedżer obiektów wywołuje metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> Aby określić, czy dany element listy jest rozwijany i ma elementy podrzędne. Jeśli interfejs użytkownika wysyła żądanie rozwinięcia elementu, Menedżer obiektów żąda podrzędnej listy symboli, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metodę. Proces jest kontynuowany z różnymi częściami drzewa tworzonego na żądanie.

> [!NOTE]
> Aby zaimplementować macierzystego dostawcę symboli kodu, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfejsów i.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: rejestrowanie biblioteki przy użyciu menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Instrukcje: uwidacznianie listy symboli udostępnianych przez bibliotekę dla menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Instrukcje: identyfikowanie symboli w bibliotece](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
