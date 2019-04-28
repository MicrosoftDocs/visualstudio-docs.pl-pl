---
title: Aktualizowanie wartości właściwości w oknie dialogowym właściwości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434192"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualizowanie wartości właściwości w oknie dialogowym właściwości
Istnieją dwa sposoby, aby zachować **właściwości** okna zsynchronizowane ze zmian wartości właściwości. Pierwszy jest wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejs, który zapewnia dostęp do funkcji obsługi okien podstawowych, w tym dostęp do i tworzenia okna dokumentów i narzędzi, które są dostarczane przez środowisko. W poniższych krokach opisano ten proces synchronizacji.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości, za pomocą elementu  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości, za pomocą interfejsu elementu  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi) dowolnym momencie tego pakietów VSPackage, projektów, lub edytorów muszą tworzyć lub wyliczenia narzędzia lub dokumentu.  
  
2. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zapewnienie **właściwości** okna zsynchronizowany ze zmianami właściwości projektu (lub innego wybranego obiektu, przeglądanie przez **właściwości** okna) bez implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i wyzwalania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzenia.  
  
3. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> i wyłączyć, odpowiednio, powiadomienie klienta zdarzeń hierarchii bez konieczności hierarchii do zaimplementowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości, za pomocą elementu IConnection  
 Drugim sposobem utrzymywania **właściwości** okna zsynchronizowane ze zmian wartości właściwości jest zaimplementowanie `IConnection` na składnika obiektu, aby wskazać istnienie wychodzących interfejsów. Jeśli chcesz zlokalizować nazwę właściwości, pochodzi z obiektu <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Wdrożenia można modyfikować deskryptorów właściwości zwraca i Zmień nazwę właściwości. Aby zlokalizować opis, Utwórz atrybut pochodzący od <xref:System.ComponentModel.DescriptionAttribute> i zastąpić właściwość Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia dotyczące implementowania interfejsu element IConnection  
  
1. `IConnection` zapewnia dostęp do obiektu podrzędnego modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. Umożliwia również dostęp do wszystkich połączeń punktu podrzędnych obiektów, każdy który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu.  
  
2. Dowolny obiekt przeglądania jest odpowiedzialny za wdrażanie <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzeń. **Właściwości** okna poinformuję dla zdarzenia ustawione za pośrednictwem `IConnection`.  
  
3. Punkt połączenia kontroluje liczbę połączeń (jeden lub więcej) pozwala ono jego implementacja obiektu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Punkt połączenia, który zezwala na tylko jeden interfejs może zwracać <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4. Klient może wywołać `IConnection` interfejs do uzyskiwania dostępu do obiektu podrzędnego modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Interfejsu może być wywoływany w celu wyliczenia punkty połączenia dla każdego interfejsu wychodzącego identyfikator (IID).  
  
5. `IConnection` również można wywołać w celu uzyskania dostępu do obiektów podrzędnych punktów połączenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs dla każdego IID wychodzących. Za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, klient rozpoczyna się lub kończy pętlę doradztwa technicznego dotyczącego z obiektu umożliwiający nawiązywanie połączeń i synchronizacją firmy klienta. Klienta można również wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu, aby uzyskać obiekt modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfejsu wyliczyć połączeń, które dysponuje informacjami.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogłoszenie wybór okna właściwości śledzenia](../misc/announcing-property-window-selection-tracking.md)   
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)