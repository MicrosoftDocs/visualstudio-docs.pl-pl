---
title: 'Instrukcje: Dostosowywanie funkcji programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a330f3c4cbe1e410ddc6a1612796c92eeda281b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016891"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Instrukcje: Dostosowywanie funkcji programu SharePoint
  Funkcje programu SharePoint można tworzyć i dostosowywać za pomocą projektanta funkcji w programie Visual Studio. Na przykład można ustawić zakres funkcji i dodać inne funkcje jako zależności. Domyślnie Projektant funkcji jest otwierany po dodaniu nowej funkcji w Eksplorator rozwiązań lub Eksploratorze pakietów programu SharePoint.

## <a name="opening-the-feature-designer"></a>Otwieranie projektanta funkcji
 Możesz dodawać lub usuwać elementy projektu programu SharePoint do funkcji za pomocą projektanta funkcji.

#### <a name="to-open-the-feature-designer"></a>Aby otworzyć projektanta funkcji

1. W **Eksplorator rozwiązań**rozwiń pozycję **funkcje**.

2. Kliknij dwukrotnie element *Feature1* lub Otwórz menu skrótów dla elementu *Feature1* , a następnie wybierz polecenie **Projektant widoków**.

## <a name="view-the-packaged-manifest-file"></a>Wyświetl spakowany plik manifestu
 Za pomocą projektanta funkcji można modyfikować i generować spakowany plik manifestu dla funkcji (*feature.xml*). Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Aby wyświetlić spakowany plik manifestu

1. W **Projektancie funkcji**wybierz kartę **manifest** .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowany plik manifestu za pomocą Eksplorator rozwiązań

1. W **Eksplorator rozwiązań**wybierz ikonę **Pokaż wszystkie pliki** .

2. Rozwiń węzeł funkcje, rozwiń element FeatureName, rozwiń pozycję FeatureName. feature, a następnie otwórz plik * \<FeatureName>.Template.xml* .

    > [!NOTE]
    > Po otwarciu pliku XML manifestu szablonu funkcji pliki są automatycznie weryfikowane i ostrzeżenia, które pojawiają się w oknie Lista błędów mogą być ignorowane.

## <a name="change-the-manifest-template"></a>Zmiana szablonu manifestu
 Kod XML dla pliku manifestu funkcji można zmienić w edytorze XML programu Visual Studio lub w okienku szablonu manifestu. Wszelkie zmiany w kodzie XML zostaną scalone z spakowanym plikiem manifestu dla tej funkcji. Na przykład możesz chcieć zmienić szablon manifestu, aby dostosować Właściwość funkcji.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić szablon manifestu przy użyciu edytora XML

1. W **Projektancie funkcji**wybierz kartę **manifest** , rozwiń węzeł **Opcje edycji** , a następnie wybierz łącze **Otwórz w edytorze XML** .

     Zmiany w kodzie XML są scalane w spakowany plik manifestu.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić szablon manifestu przy użyciu okienka szablonu manifestu

1. W **Projektancie funkcji**wybierz kartę **manifest** , rozwiń węzeł **Opcje edycji** , a następnie Zmień kod XML, który pojawia się w okienku szablon manifestu.

     Zmiany w kodzie XML pojawiają się w **wersji zapoznawczej okienka spakowanego manifestu** .

## <a name="overwrite-the-packaged-manifest-file"></a>Zastąp spakowany plik manifestu
 Projektanta funkcji można wyłączyć i ręcznie utworzyć plik *feature.xml* . Po pierwszym wykonaniu tej procedury bieżące ustawienia w Projektancie funkcji są zapisywane w pliku XML szablonu funkcji. Następnie można zmodyfikować lub zastąpić kod XML.

> [!NOTE]
> Jeśli dodasz lub usuniesz elementy projektu programu SharePoint w pliku XML, podczas gdy projektant funkcji jest wyłączony, te elementy projektu nie są spakowane.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowany plik manifestu poprzez wyłączenie projektanta

1. W **Projektancie funkcji**wybierz kartę **manifest** .

2. Rozwiń węzeł **Opcje edycji** , wybierz opcję **Zastąp wygenerowany plik XML i edytuj manifest w edytorze XML** , a następnie wybierz przycisk **tak** .

     Szablon zostanie zaktualizowany przy użyciu bieżącego spakowanego pliku manifestu.

## <a name="enable-the-feature-designer"></a>Włączanie projektanta funkcji
 Można ponownie włączyć projektanta funkcji, aby dostosować plik *feature.xml* .

#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć projektanta

1. W **Projektancie funkcji**wybierz pozycję **Odrzuć edycje manifestu i ponownie włącz link projektanta** , a następnie wybierz przycisk **tak** .

2. Szablon jest odświeżany oryginalnym tekstem i wszelkie zmiany wprowadzone w pliku XML zostaną utracone.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
