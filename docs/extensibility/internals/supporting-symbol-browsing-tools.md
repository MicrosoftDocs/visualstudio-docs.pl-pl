---
title: Narzędzia do przeglądania symboli wspierające | Dokumenty firmy Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704768"
---
# <a name="supporting-symbol-browsing-tools"></a>Obsługa narzędzi do przeglądania symboli
**Narzędzia Object Browser**, **Class View**, **Call Browser** i Find **Symbol Results** zapewniają funkcje przeglądania symboli w programie Visual Studio. Narzędzia te wyświetlają hierarchiczne widoki drzew symboli i pokazują relacje między symbolami w drzewie. Symbole mogą reprezentować przestrzenie nazw, obiekty, klasy, elementy członkowskie klasy i inne elementy języka zawarte w różnych składnikach. Składniki obejmują projekty programu Visual Studio, zewnętrzne składniki .NET Framework i biblioteki typu (.tlb). Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Biblioteki przeglądania symboli
 Jako realizator języka można rozszerzyć możliwości przeglądania symboli programu Visual Studio, tworząc biblioteki śledzące symbole w składnikach i udostępniając listy symboli menedżerowi obiektów programu Visual Studio za pośrednictwem zestawu interfejsów. Biblioteka jest opisana <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> przez interfejs. Menedżer obiektów programu Visual Studio odpowiada na żądania nowych danych z narzędzi do przeglądania symboli, uzyskując dane z bibliotek i organizując je. Następnie wypełnia lub aktualizuje narzędzia żądanymi danymi. Aby uzyskać odwołanie do menedżera obiektów <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>programu <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Visual Studio, `GetService` przekaż identyfikator usługi do metody.

 Każda biblioteka musi zarejestrować się w menedżerze obiektów programu Visual Studio, który zbiera informacje o wszystkich bibliotekach. Aby zarejestrować bibliotekę, wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. W zależności od tego, które narzędzie inicjuje żądanie, Menedżer obiektów programu Visual Studio znajduje odpowiednią bibliotekę i żąda danych. Dane są przesyłane między bibliotekami a menedżerem obiektów na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> listach symboli opisanych przez interfejs.

 Menedżer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obiektów jest odpowiedzialny za okresowe odświeżanie narzędzi do przeglądania symboli w celu odzwierciedlenia najbardziej aktualnych danych zawartych w bibliotekach.

 Poniższy diagram zawiera przykład kluczowych elementów procesu wymiany żądań/danych między biblioteką a menedżerem obiektów programu Visual Studio. Interfejsy na diagramie są częścią aplikacji kodu zarządzanego.

 ![Przepływ danych między biblioteką a menedżerem obiektów](../../extensibility/internals/media/callbrowserdiagram.gif "Diagram brwi")

 Aby udostępnić listy symboli do menedżera obiektów programu Visual Studio, należy najpierw zarejestrować <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> bibliotekę w menedżerze obiektów programu Visual Studio, wywołując metodę. Po zarejestrowaniu biblioteki menedżer obiektów programu Visual Studio żąda pewnych informacji o możliwościach biblioteki. Na przykład żąda flagi biblioteki i obsługiwane kategorie, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metody. W pewnym momencie, gdy jedno z narzędzi żąda danych z tej biblioteki, menedżer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> obiektów żąda listy symboli najwyższego poziomu, wywołując metodę. W odpowiedzi biblioteka produkuje listę symboli i udostępnia ją do menedżera <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> obiektów programu Visual Studio za pośrednictwem interfejsu. Menedżer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obiektów określa, ile elementów znajduje się <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> na liście, wywołując metodę. Wszystkie następujące żądania odnoszą się do danego elementu na liście i podają numer indeksu towaru w każdym żądaniu. Menedżer obiektów programu Visual Studio przechodzi do zbierania informacji na temat typu, ułatwień <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> dostępu i innych właściwości elementu, wywołując metodę.

 Określa nazwę elementu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metodę i żąda informacji o ikonie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> wywołując metodę. Ikona jest wyświetlana po lewej stronie nazwy elementu i przedstawia typ elementu, dostępność i inne właściwości.

 Menedżer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obiektów wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodę, aby ustalić, czy dany element listy jest rozwijalny i ma elementy podrzędne. Jeśli interfejs użytkownika wysyła żądanie, aby rozwinąć element, menedżer obiektów żąda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> listy podrzędnej symboli, wywołując metodę. Proces jest kontynuowany z różnych części drzewa budowane na żądanie.

> [!NOTE]
> Aby zaimplementować dostawcę <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> symbolu kodu macierzystego, należy użyć i interfejsów.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: rejestrowanie biblioteki przy użyciu menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Instrukcje: uwidacznianie listy symboli udostępnianych przez bibliotekę dla menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Instrukcje: identyfikowanie symboli w bibliotece](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
