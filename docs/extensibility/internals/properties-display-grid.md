---
title: Właściwości Siatki wyświetlania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706187"
---
# <a name="properties-display-grid"></a>Właściwości wyświetlają siatkę

Okno **Właściwości** wyświetla pola w siatce. Lewa kolumna zawiera nazwy właściwości; prawa kolumna zawiera wartości właściwości.

## <a name="work-with-the-grid"></a>Praca z siatką

Lista dwóch kolumn zawiera właściwości niezależne od konfiguracji, które można zmienić w czasie projektowania i ich bieżących ustawieniach. Należy zauważyć, że wszystkie właściwości mogą nie być wyświetlane. Właściwość można ustawić jako ukryte, na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> przez zaimplementowanie metody. W szczególności, aby ukryć właściwości, które mają właściwości podrzędne:

1. Ustaw `pfDisplay` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> w `FALSE`.

2. Ustaw `pfHide` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> w `TRUE`.

Aby wypchnąć informacje do okna **Właściwości,** ide używa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>jest wywoływana przez VSPackages dla każdego okna, które zawiera wybieralne obiekty z powiązanych właściwości, które mają być wyświetlane w **oknie Właściwości.** Implementacja wywołań `GetProperty` <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w **Eksploratorze rozwiązań**przy użyciu [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) w hierarchii projektów, aby uzyskać obiekty do przeglądania w hierarchii.

Jeśli vspackage nie obsługuje [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)IDE próbuje użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> wartości dla [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) które dostarczają towary lub towary hierarchii.

Projekt VSPackage nie trzeba <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> tworzyć, ponieważ pakiet okna dostarczonych IDE, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> go (na przykład **Eksplorator rozwiązań)** tworzy w jego imieniu.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>składa się z trzech metod, które są wywoływane przez IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>zawiera liczbę obiektów wybranych do wyświetlenia w oknie **Właściwości.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>zwraca `IDispatch` obiekty, które mają być wyświetlane w oknie **Właściwości.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>umożliwia wybranie dowolnego z obiektów <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> zwróconych przez użytkownika. Dzięki temu VSPackage wizualnie zaktualizować wybór wyświetlany użytkownikowi w interfejsie użytkownika.

Okno **Właściwości** wyodrębnia informacje `IDispatch` z obiektów, aby pobrać przeglądane właściwości. Przeglądarka Właściwości używa `IDispatch` do zapytać obiekt, jakie właściwości `ITypeInfo`obsługuje przez `IDispatch::GetTypeInfo`kwerendy , który jest uzyskiwany z . Przeglądarka następnie używa tych wartości do wypełniania **właściwości** okna i zmienić wartości dla poszczególnych właściwości wyświetlanych w siatce. Informacje o właściwościach są przechowywane w samym obiekcie.

Ponieważ zwracane `IDispatch`obiekty obsługują, obiekt wywołujący może uzyskać informacje, takie `IDispatch::Invoke` `ITypeInfo::Invoke` jak nazwa obiektu, wywołując albo ze wstępnie zdefiniowanym identyfikatorem wysyłki (DISPID), który reprezentuje żądane informacje. Zadeklarowane identyfikatory DISPID są ujemne, aby upewnić się, że nie są w konflikcie z identyfikatorami zdefiniowanymi przez użytkownika.

Okno **Właściwości** wyświetla różne typy pól w zależności od atrybutów określonych właściwości zaznaczonego obiektu. Pola te obejmują pola edycji, listy rozwijane i łącza do okien dialogowych edytora niestandardowego.

- Wartości zawarte na wyliczonej liście są <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> pobierane przez kwerendę do `IDispatch`. Wartości uzyskane z listy wyliczonych można zmienić w siatce właściwości, klikając dwukrotnie nazwę pola lub klikając wartość i wybierając nową wartość z listy rozwijanej. W przypadku właściwości, które mają wstępnie zdefiniowane ustawienia z wyliczonych list, dwukrotne kliknięcie nazwy właściwości na liście Właściwości przechodzi przez dostępne opcje. W przypadku wstępnie zdefiniowanych właściwości z tylko dwoma opcjami, takimi jak prawda/fałsz, kliknij dwukrotnie nazwę właściwości, aby przełączać się między opcjami.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`jest , wskazując, że wartość została zmieniona, wartość jest wyświetlana pogrubioną czcionką. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>służy do określenia, czy wartość można zresetować do oryginalnej wartości. Jeśli tak, możesz zmienić domyślną wartość, klikając ją prawym przyciskiem myszy i wybierając **polecenie Reset z** wyświetlanego menu. W przeciwnym razie należy ręcznie zmienić wartość z powrotem na domyślną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>umożliwia również lokalizowanie i ukrywanie nazw właściwości wyświetlanych w czasie projektowania, ale nie wpływa na nazwy właściwości wyświetlane w czasie wykonywania.

- Kliknięcie przycisku wielokropek (...) powoduje wyświetlenie listy wartości właściwości, z których użytkownik może wybrać (takich jak selektor kolorów lub lista czcionek). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>podaje te wartości.

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
