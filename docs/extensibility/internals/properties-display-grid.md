---
title: Właściwości Wyświetl siatkę | Microsoft Docs
description: Dowiedz się, gdzie znajdują się nazwy właściwości i pola wartości właściwości w siatce w okno Właściwości i jak pracować z siatką przy rozszerzaniu właściwości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee3d7d8d6277f9cfa0352cb4961644e4860b46bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899657"
---
# <a name="properties-display-grid"></a>Siatka wyświetlania właściwości

W **oknie** Właściwości są wyświetlane pola w siatce. Lewa kolumna zawiera nazwy właściwości. Prawa kolumna zawiera wartości właściwości.

## <a name="work-with-the-grid"></a>Praca z siatką

Lista dwóch kolumn zawiera właściwości niezależne od konfiguracji, które można zmienić w czasie projektowania i ich bieżące ustawienia. Należy pamiętać, że wszystkie właściwości mogą nie być wyświetlane. Właściwość można ustawić jako ukrytą, na przykład przez zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> metody . W szczególności, aby ukryć właściwości, które mają właściwości podrzędne:

1. Ustaw parametr `pfDisplay` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> parametrze na `FALSE` wartość .

2. Ustaw parametr `pfHide` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> parametrze na `TRUE` wartość .

Aby wypchnąć informacje do **okna Właściwości,** w ide używane jest . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Jest wywoływana przez pakiet VSPackages dla każdego okna zawierającego obiekty z właściwościami, które można wybierać, które mają być wyświetlane w **oknie** Właściwości. **Eksplorator rozwiązań** implementacji wywołań <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> przy `GetProperty` użyciu [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) w hierarchii projektu, aby uzyskać obiekty, które można przeglądać w hierarchii.

Jeśli pakiet VSPackage nie obsługuje [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)ide próbuje użyć wartości dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) który dostarcza element lub elementy hierarchii.

Nie trzeba tworzyć pakietu VSPackage projektu, ponieważ w jego imieniu jest konstruowana konstrukcja pakietu okien dostarczonego przez ideę , który go <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> implementuje (na przykład **Eksplorator rozwiązań**). <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Metoda składa się z trzech metod wywoływanych przez ideę IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> Zawiera liczbę obiektów wybranych do wyświetlania w **oknie** Właściwości.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Zwraca obiekty `IDispatch` wybrane do wyświetlania w **oknie** Właściwości.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> umożliwia, aby dowolny z obiektów zwróconych przez element <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> został wybrany przez użytkownika. Dzięki temu pakiet VSPackage może wizualnie zaktualizować wybór wyświetlany użytkownikowi w interfejsie użytkownika.

Okno **Właściwości** wyodrębnia informacje z `IDispatch` obiektów w celu pobrania przeglądanych właściwości. Przeglądarka Właściwości używa obiektu , aby zadać obiektowi pytanie, jakie właściwości obsługuje, odpytując `IDispatch` obiekt , który jest `ITypeInfo` uzyskiwany z obiektu `IDispatch::GetTypeInfo` . Następnie przeglądarka używa tych wartości do wypełnienia okna **Właściwości** i zmiany wartości poszczególnych właściwości wyświetlanych w siatce. Informacje o właściwościach są zachowywane w obrębie samego obiektu.

Ponieważ zwracane obiekty obsługują obiekt , obiekt wywołujący może uzyskać informacje, takie jak nazwa obiektu, wywołując albo za pomocą wstępnie zdefiniowanego identyfikatora wysyłania (DISPID), który reprezentuje `IDispatch` `IDispatch::Invoke` `ITypeInfo::Invoke` żądane informacje. Zadeklarowane identyfikatory DISPID są ujemne, aby upewnić się, że nie kolidują z identyfikatorami zdefiniowanymi przez użytkownika.

W **oknie** Właściwości są wyświetlane różne typy pól w zależności od atrybutów określonych właściwości wybranego obiektu. Pola te obejmują pola edycji, listy rozwijane i linki do okien dialogowych edytora niestandardowego.

- Wartości zawarte na wyliczeniowej liście są pobierane przez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> zapytanie do `IDispatch` . Wartości uzyskane z listy wyliczeniowej można zmienić w siatce właściwości, klikając dwukrotnie nazwę pola lub klikając wartość i wybierając nową wartość z listy rozwijanej. W przypadku właściwości, które mają wstępnie zdefiniowane ustawienia z list wyliczeniowych, dwukrotne kliknięcie nazwy właściwości na liście Właściwości wyświetla dostępne opcje. W przypadku wstępnie zdefiniowanych właściwości z tylko dwoma wyborami, takimi jak prawda/fałsz, kliknij dwukrotnie nazwę właściwości, aby przełączać się między wyborami.

- Jeśli wartość to , oznacza to, że wartość <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> została zmieniona, wartość jest `false` wyświetlana w tekście pogrubionym. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> Służy do określania, czy można zresetować wartość do oryginalnej wartości. Jeśli tak, możesz wrócić do wartości domyślnej, klikając prawym przyciskiem myszy wartość i wybierając polecenie **Resetuj** z wyświetlonego menu. W przeciwnym razie należy ręcznie zmienić wartość z powrotem na wartość domyślną. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Umożliwia także lokalizacji i ukrywanie nazw właściwości wyświetlanych w czasie projektowania, ale nie ma wpływu na nazwy właściwości wyświetlane w czasie uruchamiania.

- Kliknięcie przycisku wielokropka (...) powoduje wyświetlenie listy wartości właściwości, z których użytkownik może wybrać (na przykład selektor kolorów lub lista czcionek). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Udostępnia te wartości.

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
