---
title: Obsługa narzędzi do przeglądania symboli | Microsoft Docs
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723079"
---
# <a name="supporting-symbol-browsing-tools"></a>Obsługa narzędzi do przeglądania symboli
**Przeglądarka obiektów**, **Widok klasy**, **przeglądarka wywołań** i **Znajdź narzędzia wyników symboli** zapewniają możliwości przeglądania symboli w programie Visual Studio. Te narzędzia wyświetlają hierarchiczne widoki drzewa symboli i pokazują relacje między symbolami w drzewie. Symbole mogą reprezentować przestrzenie nazw, obiekty, klasy, składowe klas i inne elementy języka zawarte w różnych składnikach. Składniki obejmują projekty programu Visual Studio, zewnętrzne składniki .NET Framework i biblioteki typu (. tlb). Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Biblioteki przeglądania symboli
 Jako implementujący język można rozciągnąć możliwości przeglądania symboli programu Visual Studio, tworząc biblioteki, które śledzą symbole w składnikach i dostarczają listę symboli do Menedżera obiektów programu Visual Studio za pomocą zestawu interfejsów. Biblioteka jest opisana przez interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>. Menedżer obiektów programu Visual Studio reaguje na żądania nowych danych z narzędzi do przeglądania symboli, uzyskując dane z bibliotek i organizując je. Następnie wypełnia i aktualizuje narzędzia przy użyciu żądanych danych. Aby uzyskać odwołanie do Menedżera obiektów programu Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, Przekaż identyfikator usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> do metody `GetService`.

 Każda biblioteka musi być zarejestrowana w Menedżerze obiektów programu Visual Studio, który gromadzi informacje we wszystkich bibliotekach. Aby zarejestrować bibliotekę, wywołaj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. W zależności od tego, które narzędzie inicjuje żądanie, Menedżer obiektów programu Visual Studio znajduje odpowiednią bibliotekę i żąda danych. Dane przesyłane między bibliotekami i menedżerem obiektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajdują się na liście symboli opisanych przez interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>.

 Menedżer obiektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest odpowiedzialny za okresowe odświeżanie narzędzi do przeglądania symboli w celu odzwierciedlenia najbardziej aktualnych danych zawartych w bibliotekach.

 Poniższy diagram zawiera przykład kluczowych elementów procesu żądania/wymiany danych między biblioteką i menedżerem obiektów programu Visual Studio. Interfejsy na diagramie są częścią aplikacji kodu zarządzanego.

 ![Przepływ danych między biblioteką a menedżerem obiektów](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Aby udostępnić listę symboli dla Menedżera obiektów programu Visual Studio, należy najpierw zarejestrować bibliotekę w Menedżerze obiektów Visual Studio, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. Po zarejestrowaniu biblioteki Menedżer obiektów programu Visual Studio żąda pewnych informacji o możliwościach biblioteki. Na przykład żąda flag biblioteki i obsługiwanych kategorii przez wywołanie metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>. W pewnym momencie, gdy jeden z narzędzi żąda danych z tej biblioteki, Menedżer obiektów żąda listy symboli najwyższego poziomu, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>. W odpowiedzi Biblioteka tworzy listę symboli i udostępnia ją menedżerowi obiektów programu Visual Studio za pomocą interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>. Menedżer obiektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określa, ile elementów znajduje się na liście, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>. Wszystkie poniższe żądania odnoszą się do danego elementu na liście i podają numer indeksu elementu w każdym żądaniu. Menedżer obiektów programu Visual Studio będzie kontynuował zbieranie informacji o typie, dostępności i innych właściwościach elementu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>.

 Określa nazwę elementu, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> i żąda informacji o ikonie poprzez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>. Ikona jest wyświetlana po lewej stronie nazwy elementu i przedstawia typ elementu, ułatwienia dostępu i inne właściwości.

 Menedżer obiektów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wywołuje metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>, aby określić, czy dany element listy jest rozszerzalny i ma elementy podrzędne. Jeśli interfejs użytkownika wysyła żądanie rozwinięcia elementu, Menedżer obiektów żąda podrzędnej listy symboli, wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>. Proces jest kontynuowany z różnymi częściami drzewa tworzonego na żądanie.

> [!NOTE]
> Aby zaimplementować macierzystego dostawcę symboli kodu, użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfejsów.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: rejestrowanie biblioteki przy użyciu menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Instrukcje: uwidacznianie listy symboli udostępnianych przez bibliotekę dla menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Instrukcje: identyfikowanie symboli w bibliotece](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)