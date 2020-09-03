---
title: Siatka wyświetlania właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180382"
---
# <a name="properties-display-grid"></a>Siatka wyświetlania właściwości
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **Właściwości** wyświetla pola w obrębie siatki. Lewa kolumna zawiera nazwy właściwości; prawa kolumna zawiera wartości właściwości.  
  
## <a name="working-with-the-grid"></a>Praca z siatką  
 Lista dwóch kolumn zawiera niezależne od konfiguracji właściwości, które można zmieniać w czasie projektowania i ich bieżące ustawienia. Należy zauważyć, że wszystkie właściwości mogą nie być wyświetlane. Właściwość można ustawić jako ukrytą, na przykład przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody. Aby ukryć właściwości, które mają właściwości podrzędne, zobacz [ukrywanie właściwości, które mają właściwości podrzędne](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Aby wypchnąć informacje do okna **Właściwości** , środowisko IDE używa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> jest wywoływany przez pakietów VSPackage dla każdego okna, które zawiera obiekty możliwe do wybrania z powiązanymi właściwościami, które mają być wyświetlane w oknie **Właściwości** . **Eksplorator rozwiązań**implementacja <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wywołań `GetProperty` przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> w hierarchii projektu w celu uzyskania obiektów do przeglądania w hierarchii.  
  
 Jeśli pakietu VSPackage nie obsługuje <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , IDE próbuje użyć wartości, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> dostarczyć element lub elementy hierarchii.  
  
 Projekt pakietu VSPackage nie musi być tworzony, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ponieważ pakiet okna dostarczony przez IDE, który implementuje go (na przykład **Eksplorator rozwiązań**) konstrukcje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w jego imieniu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> składa się z trzech metod, które są wywoływane przez IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> zawiera liczbę obiektów wybranych do wyświetlenia w oknie **Właściwości** .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> zwraca `IDispatch` obiekty, które są wybrane do wyświetlenia w oknie **Właściwości** .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> sprawia, że jest to możliwe dla każdego obiektu zwróconego przez element <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> do wybranego przez użytkownika. Dzięki temu pakietu VSPackage można wizualnie zaktualizować wybór wyświetlany użytkownikowi w INTERFEJSie użytkownika.  
  
  Okno **Właściwości** wyodrębnia informacje z `IDispatch` obiektów w celu pobrania właściwości, które są przeglądane. Właściwości przeglądarki używa `IDispatch` do podawania obiektu właściwości, które obsługuje przez zapytania `ITypeInfo` , które są uzyskiwane z `IDispatch::GetTypeInfo` . Następnie przeglądarka używa tych wartości, aby wypełnić okno **Właściwości** i zmienić wartości poszczególnych właściwości wyświetlanych w siatce. Informacje o właściwościach są przechowywane w samym obiekcie.  
  
  Ponieważ zwrócone obiekty obsługują `IDispatch` , wywołujący może uzyskać informacje takie jak nazwa obiektu przez wywołanie albo `IDispatch::Invoke` `ITypeInfo::Invoke` ze wstępnie zdefiniowanym identyfikatorem wysyłania (DISPID), który reprezentuje żądane informacje. Zadeklarowane identyfikatory SPID są ujemne, aby nie powodowały konfliktów z identyfikatorami zdefiniowanymi przez użytkownika.  
  
  Okno **Właściwości** wyświetla różne typy pól w zależności od atrybutów określonych właściwości wybranego obiektu. Te pola obejmują pola edycji, listy rozwijane i linki do okien dialogowych edytorów niestandardowych.  
  
- Wartości zawarte na liście wyliczane są pobierane przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> zapytanie do `IDispatch` . Wartości uzyskanych z listy wyliczanej można zmienić w siatce właściwości przez dwukrotne kliknięcie nazwy pola lub kliknięcie wartości i wybranie nowej wartości z listy rozwijanej. W przypadku właściwości, które mają wstępnie zdefiniowane ustawienia z list wyliczanych, dwukrotnie kliknij nazwę właściwości na liście właściwości, przechodząc do opcji dostępne opcje. Dla wstępnie zdefiniowanych właściwości z tylko dwoma opcjami, takimi jak true/false, kliknij dwukrotnie nazwę właściwości, aby przełączać się między wybranymi opcjami.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> jest `false` , wskazując, że wartość została zmieniona, wartość jest wyświetlana pogrubioną czcionką. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> służy do określenia, czy wartość może zostać zresetowana do wartości oryginalnej. W takim przypadku można zmienić wartość domyślną, klikając prawym przyciskiem myszy tę pozycję i wybierając pozycję **Zresetuj** z wyświetlonego menu. W przeciwnym razie należy ręcznie zmienić wartość z powrotem na domyślną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> umożliwia również lokalizowanie i ukrywanie nazw właściwości wyświetlanych w czasie projektowania, ale nie wpływa na nazwy właściwości wyświetlane w czasie wykonywania.  
  
- Kliknięcie przycisku wielokropka (...) powoduje wyświetlenie listy wartości właściwości, z których użytkownik może wybrać (na przykład selektor kolorów lub Lista czcionek). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> zawiera te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
