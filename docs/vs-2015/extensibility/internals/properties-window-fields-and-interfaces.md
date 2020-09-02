---
title: Pola i interfejsy okna właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700820"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model wyboru służący do określania, jakie informacje są wyświetlane w oknie **Właściwości** , zależy od okna, które ma fokus w środowisku IDE. Każde okno i obiekt w wybranym oknie może mieć obiekt kontekstu zaznaczenia wypychany do globalnego kontekstu wyboru. Środowisko aktualizuje globalny kontekst wyboru przy użyciu wartości z ramki okna, gdy to okno ma fokus. Gdy fokus zmieni się, oznacza to, że kontekst zaznaczenia.  
  
## <a name="tracking-selection-in-the-ide"></a>Śledzenie wyboru w środowisku IDE  
 W przypadku ramki okna lub lokacji należącej do IDE jest wywoływana usługa <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Poniższe kroki pokazują, jak zmiana w wyborze, spowodowana przez użytkownika zmiana fokusu na inne otwarte okno lub wybranie innego elementu projektu w **Eksplorator rozwiązań**, jest zaimplementowana w celu zmiany zawartości wyświetlanej w oknie **Właściwości** .  
  
1. Obiekt utworzony przez pakietu VSPackage, który jest zlokalizowany w wybranym oknie wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> do wywołania metody <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Kontener wyboru udostępniony przez wybrane okno tworzy własny <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiekt. Po zmianie zaznaczenia pakietu VSPackage wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> powiadomienia o wszelkich detektorach w środowisku, w tym okna **Właściwości** zmiany. Zapewnia również dostęp do informacji o hierarchii i elementu związanych z nowym wyborem.  
  
3. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie do niego wybranych elementów hierarchii w `VSHPROPID_BrowseObject` parametrze wypełnia <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiekt.  
  
4. Obiekt pochodny [interfejsu IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) jest zwracany dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> elementu w żądanym elemencie, a środowisko zawija je do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (zobacz poniższy krok). Jeśli wywołanie zakończy się niepowodzeniem, środowisko wykonuje drugie wywołanie `IVsHierarchy::GetProperty` , przekazując do niego kontener wyboru, <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> który dostarcza element lub elementy hierarchii.  
  
    Projekt pakietu VSPackage nie jest tworzony <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , ponieważ okno dostarczone przez środowisko pakietu VSPackage, które implementuje go (na przykład **Eksplorator rozwiązań**) konstrukcje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jego imieniu.  
  
5. Środowisko wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w celu uzyskania obiektów opartych na `IDispatch` interfejsie do wypełnienia w oknie **Właściwości** .  
  
   Gdy wartość w oknie **Właściwości** zostanie zmieniona, pakietów VSPackage zaimplementować `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` Aby zgłosić zmianę wartości elementu. Środowisko następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lub, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Aby zachować informacje wyświetlane w oknie **Właściwości** zsynchronizowane z wartościami właściwości. Aby uzyskać więcej informacji, zobacz [aktualizowanie wartości właściwości w oknie właściwości](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Oprócz wyboru innego elementu projektu w **Eksplorator rozwiązań** , aby wyświetlić właściwości powiązane z tym elementem, można również wybrać inny obiekt z poziomu formularza lub dokumentu przy użyciu listy rozwijanej dostępnej w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).  
  
   Można zmienić sposób wyświetlania informacji w siatce okna **Właściwości** z alfabetyczne do kategorii i, jeśli jest dostępny, można także otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednie przyciski w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md) i [strony właściwości](../../extensibility/internals/property-pages.md).  
  
   Wreszcie Dolna część okna **Właściwości** zawiera również opis pola zaznaczonego w siatce okna **Właściwości** . Aby uzyskać więcej informacji, zobacz [pobieranie opisów pól z okna właściwości](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
