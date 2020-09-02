---
title: Aktualizowanie wartości właściwości w oknie właściwości | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434192"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualizowanie wartości właściwości w oknie właściwości
Istnieją dwa sposoby, aby zachować synchronizację okna **Właściwości** ze zmianami wartości właściwości. Pierwszym jest wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu, który zapewnia dostęp do podstawowych funkcji okna, w tym dostęp do i tworzenie narzędzi i dokumentów systemu Windows udostępnianych w środowisku. Poniższe kroki opisują ten proces synchronizacji.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości przy użyciu IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości przy użyciu interfejsu IVsUIShell  
  
1. Wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (za poorednictwem <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi) w dowolnym momencie, gdy pakietów VSPackage, projekty lub edytory muszą tworzyć lub wyliczać okna narzędzi lub dokumentów.  
  
2. Zaimplementuj, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Aby zachować synchronizację okna **Właściwości** ze zmianami właściwości dla projektu (lub dowolnym innym wybranym obiektem przeglądanym przez okno **Właściwości** ) bez implementowania <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i uruchamiania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzeń.  
  
3. Wdrażaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> ustanawiaj i wyłączaj odpowiednio powiadomienia klienta dotyczące zdarzeń hierarchii bez konieczności implementowania hierarchii <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości przy użyciu IConnection  
 Drugi sposób utrzymywania okna **Właściwości** w synchronizacji ze zmianami wartości właściwości ma na celu zaimplementowanie `IConnection` w obiekcie połączonym, aby wskazać istnienie interfejsów wychodzących. Jeśli chcesz zlokalizować nazwę właściwości, Utwórz obiekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . <xref:System.ComponentModel.ICustomTypeDescriptor>Implementacja może zmodyfikować deskryptory właściwości, które zwraca i zmienić nazwę właściwości. Aby zlokalizować opis, Utwórz atrybut pochodzący z <xref:System.ComponentModel.DescriptionAttribute> i Zastąp Właściwość Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia dotyczące implementacji interfejsu IConnection  
  
1. `IConnection` zapewnia dostęp do podrzędnego obiektu modułu wyliczającego za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu. Zapewnia również dostęp do wszystkich podobiektów punktu połączenia, z których każdy implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs.  
  
2. Każdy obiekt przeglądania jest odpowiedzialny za implementację <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzenia. Okno **Właściwości** zostanie powiadomione o zdarzeniu ustawionym przez `IConnection` .  
  
3. Punkt połączenia kontroluje liczbę połączeń (co najmniej jeden), które umożliwia w jego implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Punkt połączenia, który dopuszcza tylko jeden interfejs, może zwracać <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody.  
  
4. Klient może wywołać interfejs, `IConnection` Aby uzyskać dostęp do podrzędnego obiektu modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsem. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>Interfejs można następnie wywołać, aby wyliczyć punkty połączenia dla każdego identyfikatora interfejsu wychodzącego (IID).  
  
5. `IConnection` może być również wywoływana w celu uzyskania dostępu do podobiektów punktu połączenia z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsem dla każdego wychodzącego identyfikatora IID. Za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu klient uruchamia lub kończy pętlę doradczą z obiektem połączonym i synchronizacją klienta. Klient może również wywołać interfejs, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Aby uzyskać obiekt modułu wyliczającego z <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfejsem, aby wyliczyć połączenia, o których wie.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogłoszenie śledzenia wyboru okna właściwości](../misc/announcing-property-window-selection-tracking.md)   
 [Rozszerzanie właściwości](../extensibility/internals/extending-properties.md)