---
title: 'Instrukcje: Dostosowywanie funkcji SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: ddf2d14d8241f35ac0d83cb0a7f4dab0dd3f6f32
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618188"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Instrukcje: Dostosowywanie funkcji SharePoint
  Można tworzyć i dostosowywać funkcje programu SharePoint przy użyciu narzędzia Projektant funkcji w programie Visual Studio. Na przykład można ustawić zakres funkcji i dodać inne funkcje jako zależności. Domyślnie Projektant funkcji jest otwierany podczas dodawania nowej funkcji w Eksploratorze rozwiązań lub w Eksploratorze pakietu programu SharePoint.

## <a name="opening-the-feature-designer"></a>Otwieranie Projektanta funkcji
 Elementy projektu programu SharePoint można dodawać do i usuwać z funkcji przy użyciu narzędzia Projektant funkcji.

#### <a name="to-open-the-feature-designer"></a>Aby otworzyć Projektanta funkcji

1.  W **Eksploratorze rozwiązań** rozwiń węzeł **Funkcje**.

2.  Kliknij dwukrotnie element *Feature1* lub otwórz menu skrótów elementu *Feature1*, a następnie wybierz pozycję **Widok projektanta**.

## <a name="view-the-packaged-manifest-file"></a>Wyświetlanie spakowanego pliku manifestu
 Projektant funkcji może służyć do modyfikacji i generowania pliku manifestu spakowanych funkcji (*feature.xml*). Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Aby wyświetlić spakowany pliku manifestu

1.  W **Projektancie funkcji** wybierz kartę **Manifest**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowany plik manifestu za pomocą Eksploratora rozwiązań

1.  W **Eksploratorze rozwiązań** wybierz ikonę **Pokaż wszystkie pliki**.

2.  Rozwiń węzeł Funkcje, rozwiń pozycję NazwaFunkcji, rozwiń pozycję NazwaFunkcji.feature, a następnie otwórz plik  *\<Nazwa_funkcji >. Template.XML* .

    > [!NOTE]
    >  Po otwarciu szablonu manifestu funkcji w formacie pliku XML pliki zostaną automatycznie sprawdzone i można zignorować ostrzeżenia, które są wyświetlane w oknie Lista błędów.

## <a name="change-the-manifest-template"></a>Zmiana szablonu manifestu
 Kod XML pliku manifestu funkcji można zmienić w edytorze XML programu Visual Studio lub w okienku szablonu manifestu. Wszelkie zmiany w kodzie XML są scalane do spakowanego pliku manifestu funkcji. Na przykład można zmienić szablon manifestu, aby dostosować właściwość funkcji.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić szablon manifestu za pomocą edytora XML

1.  W **Projektancie funkcji** wybierz kartę **Manifest**, rozwiń węzeł **Opcje edycji**, a następnie wybierz link **Otwórz w edytorze XML**.

     Zmiany w pliku XML są scalane w spakowanym pliku manifestu.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić szablon manifestu przy użyciu okienka szablonu manifestu

1.  W **Projektancie funkcji** wybierz kartę **Manifest**, rozwiń węzeł **Opcje edycji**, a następnie zmień plik XML, który zostanie wyświetlony w okienku manifestu szablonu.

     Zmiany w pliku XML są wyświetlane w okienku **Podgląd spakowanego manifestu**.

## <a name="overwrite-the-packaged-manifest-file"></a>Zastąpienie spakowanego pliku manifestu
 Można wyłączyć Projektanta funkcji i utworzyć plik *feature.xml* ręcznie. Podczas pierwszego wykonywania tej procedury bieżące ustawienia Projektanta funkcji są zapisywane do pliku XML szablonu funkcji. Następnie można zmodyfikować lub zastąpić ten kod XML.

> [!NOTE]
>  Jeśli dodasz lub usuniesz elementy projektu SharePoint w pliku XML, gdy Projektant funkcji jest wyłączony, te elementy projektu nie zostaną spakowane.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowany plik manifestu poprzez wyłączenie projektanta

1.  W **Projektancie funkcji** wybierz kartę **Manifest**.

2.  Rozwiń węzeł **Opcje edycji**, wybierz link **Zastąp wygenerowany kod XML i edytuj manifest w edytorze XML**, a następnie wybierz przycisk **Tak**.

     Szablon zostanie zaktualizowany o spakowany plik bieżącego manifestu.

## <a name="enable-the-feature-designer"></a>Włączanie Projektanta funkcji
 Można ponownie włączyć Projektanta funkcji, aby dostosować plik *feature.xml*.

#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć Projektanta

1.  W **Projektancie funkcji** wybierz link **Odrzuć zmiany manifestu i ponownie włącz projektanta**, a następnie wybierz przycisk **Tak**.

2.  Szablon zostanie odświeżony z początkowym tekstem, a zmiany wprowadzone w pliku XML zostaną utracone.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
