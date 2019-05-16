---
title: Właściwości pola i interfejsy okna | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700820"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Model do wyboru ustalić, jakie informacje są wyświetlane w **właściwości** okna opiera się na okno, które ma fokus w środowisku IDE. Każdego okna, a obiekt w obrębie wybranego okna może mieć jego obiekt kontekstu wyboru wypchnięte do kontekst zaznaczenia globalnego. Środowisko aktualizuje kontekst zaznaczenia globalnych z wartościami z ramki okna, gdy to okno ma fokus. Po zmianie fokusu kończy kontekst zaznaczenia.  
  
## <a name="tracking-selection-in-the-ide"></a>Śledzenie zaznaczenia w środowisku IDE  
 Ramka okna lub lokacji należących do środowiska IDE, ma usługi o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Poniższe kroki pokazują, jak zmiany w wyborze spowodowane przez użytkownika, zmiana fokusu do innego otwartego okna lub wybraniu elementu innego projektu w **Eksploratora rozwiązań**, zaimplementowany, aby zmienić zawartość wyświetlaną w  **Właściwości** okna.  
  
1. Obiekt utworzony przez Twojego pakietu VSPackage, który jest zlokalizowany w wywołaniach wybrane okno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> mieć <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> wywołania <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Kontener wyboru, dostarczone przez wybrane okno tworzy własne <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu. Gdy zostanie zmieniony na wybór pakietu VSPackage wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> o dowolnym w środowisku, w tym **właściwości** okna zmiany. Umożliwia także dostęp do informacji o hierarchii i elementów związanych z nowe zaznaczenie.  
  
3. Wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie do niej elementy na wybraną hierarchię `VSHPROPID_BrowseObject` wypełnia parametr <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiektu.  
  
4. Obiekt pochodzi od [interfejsu IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) jest zwracany w przypadku <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> dla żądanego elementu, a środowisko jest zawijany do <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (patrz następny krok). Jeśli wywołanie zakończy się niepowodzeniem, środowiska sprawia, że drugie wywołanie `IVsHierarchy::GetProperty`, przekazanie jej w kontenerze zaznaczenia <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> podać hierarchii element lub elementy.  
  
    Projektu pakietu VSPackage nie powoduje utworzenia <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ okno dostarczane przez środowisko pakietu VSPackage, który zawiera go (na przykład **Eksploratora rozwiązań**) tworzy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jej imieniu.  
  
5. Środowisko wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> można pobrać obiektów na podstawie `IDispatch` interfejsu, aby wypełnić **właściwości** okna.  
  
   Gdy wartość w **właściwości** okno zostanie zmieniony, implementować pakietów VSPackage `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` do zgłoszenia tej zmiany wartości elementu. Następnie wywołuje środowisko <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> lub <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> zapewnienie informacji wyświetlanych w **właściwości** okna synchronizowane z wartości właściwości. Aby uzyskać więcej informacji, zobacz [aktualizacji wartości właściwości w oknie dialogowym właściwości](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Oprócz wybierając inny element projektu w **Eksploratora rozwiązań** Aby wyświetlić właściwości powiązanych z tego elementu, można także innego obiektu z okna formularza lub dokumentu za pomocą listy rozwijanej, dostępne w **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).  
  
   Możesz zmienić sposób wyświetlania informacji w **właściwości** siatki okna z alfabetycznym do kategorii, a jeśli to możliwe, można także otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednią przyciski na  **Właściwości** okna. Aby uzyskać więcej informacji, zobacz [przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md) i [stron właściwości](../../extensibility/internals/property-pages.md).  
  
   Na koniec dołu **właściwości** okno zawiera również opis pola wybranego w **właściwości** siatki okna. Aby uzyskać więcej informacji, zobacz [wprowadzenie opisy pól z okna właściwości](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
