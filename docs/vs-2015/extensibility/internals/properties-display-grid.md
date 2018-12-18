---
title: Wyświetlanie właściwości siatki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a3db18bacb2aee7bd908be4246c1ce0701e8fee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741388"
---
# <a name="properties-display-grid"></a>Siatka wyświetlania właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Właściwości** okna wyświetla pola w obrębie siatki. Lewa kolumna zawiera nazwy właściwości; prawa kolumna zawiera wartości właściwości.  
  
## <a name="working-with-the-grid"></a>Praca z siatki  
 Lista dwie kolumny zawiera właściwości niezależne od konfiguracji, które można zmieniać w czasie projektowania i ich bieżących ustawień. Należy pamiętać, że wszystkie właściwości mogą być niewidoczne. Można ustawić właściwości jako ukryte, na przykład dzięki zaimplementowaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. W szczególności do właściwości Ukryj, które mają właściwości podrzędnej znajduje się pozycja [ukrywanie właściwości, mieć właściwości podrzędnej](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Do wypychania informacji do **właściwości** okno, IDE używa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest wywoływana przez pakietów VSPackage dla każdego okna, który zawiera obiekty można wybierać z powiązanych właściwości, które mają być wyświetlane w **właściwości** okna. **Eksplorator rozwiązań**przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wywołania `GetProperty` przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> w hierarchii projektu w celu uzyskania przeglądane obiektów w hierarchii.  
  
 Jeśli nie obsługuje Twojego pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, IDE podejmują próbę użycia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> przy użyciu wartości dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> podać hierarchii element lub elementy.  
  
 Projektu pakietu VSPackage nie trzeba tworzyć <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ pakiet okna dostarczane przez środowisko IDE, implementuje go (na przykład **Eksploratora rozwiązań**) tworzy <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jej imieniu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> składa się z trzech metod, które są wywoływane przez środowisko IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> zawiera liczbę obiekty wybrane do wyświetlenia w **właściwości** okna.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Zwraca `IDispatch` obiekty, które są wybrane do wyświetlenia w **właściwości** okna.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> Umożliwia dowolny obiekt zwrócony przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> do wybrania przez użytkownika. Dzięki temu pakietu VSPackage wizualnie zaktualizować wyboru widoczny dla użytkowników w interfejsie użytkownika.  
  
  **Właściwości** okna wyodrębnia dane z `IDispatch` obiektów, które można pobrać właściwości są przeglądane. Przez przeglądarkę właściwości `IDispatch` poprosić obiektu właściwości obsługuje, badając `ITypeInfo`, które są uzyskiwane z `IDispatch::GetTypeInfo`. Następnie używa tych wartości do wypełniania w przeglądarce **właściwości** okna i zmień wartości dla poszczególnych właściwości wyświetlane w siatce. Informacje o właściwościach jest zachowywana w obrębie samego obiektu.  
  
  Ponieważ zwracanych obiektów obsługuje `IDispatch`, obiekt wywołujący można uzyskać informacje, takie jak nazwy obiektu przez wywołanie metody albo `IDispatch::Invoke` lub `ITypeInfo::Invoke` o identyfikatorze wysyłania wstępnie zdefiniowane (identyfikator DISPID) reprezentuje żądane informacje. Zadeklarowane DISPID jest ujemna, aby upewnić się, że nie powodują konfliktów z identyfikatorami zdefiniowanych przez użytkownika.  
  
  **Właściwości** oknie wyświetlane różne typy pól, w zależności od atrybutów specjalnych właściwości obiektu wybranego obiektu. Tych pól należą pola tekstowe, listy rozwijane i łącza do niestandardowego edytora okien dialogowych.  
  
- Wartości zawarte w liście wyliczany są pobierane przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> zapytania `IDispatch`. W siatce właściwości można zmienić wartości z liście wyliczany, klikając dwukrotnie nazwę pola lub klikając wartość i wybierając nową wartość z listy rozwijanej. Dla właściwości, które zostały wstępnie zdefiniowane ustawienia z wyliczanych list klikając dwukrotnie nazwę właściwości, na liście właściwości przewijać dostępnych opcji. Wstępnie zdefiniowane właściwości tylko dwie opcje, takie jak PRAWDA/FAŁSZ kliknij dwukrotnie nazwę właściwości, aby przełączać się między wyborów.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> jest `false`, wskazującą, czy wartość została zmieniona, wartość jest wyświetlana czcionką pogrubioną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Służy do określenia, jeśli wartość można przywrócić oryginalną wartość. Jeśli tak, możesz zmienić domyślną, kliknij prawym przyciskiem myszy wartość i wybierając pozycję **resetowania** z wyświetlonego menu. W przeciwnym razie należy ręcznie zmienić wartość domyślną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Umożliwia także lokalizowanie i Ukryj nazwy właściwości wyświetlane w czasie projektowania, ale nie ma wpływu na nazwy właściwości wyświetlane w czasie wykonywania.  
  
- Klikając przycisk wielokropka (...) Wyświetla listę wartości właściwości, z których użytkownik może wybrać (na przykład selektora kolorów lub Lista czcionek). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> udostępnia te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)

