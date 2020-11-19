---
title: 'Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint | Microsoft Docs'
description: Użyj projektanta pakietów do tworzenia i dostosowywania pakietu rozwiązań programu SharePoint (wsp). Wyświetl lub Zastąp spakowany plik manifestu. Zmień szablon manifestu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7055be0b089a0b7c582ef0b66d84951d01685870
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903640"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint
  Można użyć projektanta pakietów do tworzenia i dostosowywania pakietu (*. wsp*). Można na przykład dodać elementy i funkcje projektu programu SharePoint, określić, czy serwer sieci Web ma być resetowany po wdrożeniu rozwiązania, i ustawić typ serwera wdrażania.

## <a name="open-the-package-designer"></a>Otwórz projektanta pakietów

#### <a name="to-open-the-package-designer"></a>Aby otworzyć projektanta pakietów

- W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję **pakiet** lub wybierz pozycję **Widok projektanta** w menu skrótów **pakietu**.

## <a name="view-the-packaged-manifestffile"></a>Wyświetl spakowany manifestfFile
 Za pomocą projektanta pakietów można modyfikować i generować spakowany plik manifestu. Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Aby wyświetlić plik źródłowy XML

1. W **projektancie pakietów** wybierz pozycję **manifest**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowany plik manifestu za pomocą Eksplorator rozwiązań

1. W **Eksplorator rozwiązań** wybierz opcję **Pokaż wszystkie pliki**.

2. Rozwiń węzeł pakiet, rozwiń pozycję pakiet. pakiet, a następnie otwórz plik *Package.Template.xml* .

    > [!NOTE]
    > Po otwarciu pliku XML manifestu dla szablonu pakietu pliki są automatycznie sprawdzane i można zignorować ostrzeżenia, które pojawiają się w oknie Lista błędów.

## <a name="change-the-manifest-template"></a>Zmiana szablonu manifestu
 Kod XML dla spakowanego pliku manifestu można zmienić w edytorze XML programu Visual Studio lub w okienku szablonu manifestu. Wszelkie zmiany w kodzie XML są scalane do spakowanego pliku manifestu pakietu.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić szablon manifestu przy użyciu edytora XML

1. W **projektancie pakietów** wybierz kartę **manifest** , rozwiń węzeł **Opcje edycji** , a następnie wybierz łącze **Otwórz w edytorze XML** .

     Zmiany w kodzie XML są scalane w spakowany plik manifestu.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić szablon manifestu przy użyciu okienka szablonu manifestu

1. W **projektancie pakietów** wybierz kartę **manifest** , rozwiń węzeł **Opcje edycji** , a następnie Zmień kod XML, który pojawia się w okienku szablon manifestu.

     Zmiany w kodzie XML pojawiają się w **wersji zapoznawczej okienka spakowanego manifestu** .

## <a name="overwrite-the-packaged-manifest-file"></a>Zastąp spakowany plik manifestu
 Można wyłączyć projektanta pakietów i ręcznie utworzyć plik *manifest.xml* . Po pierwszym wykonaniu tej procedury bieżące ustawienia w projektancie pakietów są zapisywane w pliku XML szablonu pakietu. Następnie można zmodyfikować lub zastąpić kod XML.

> [!NOTE]
> Jeśli dodasz lub usuniesz elementy projektu programu SharePoint i funkcje w pliku XML, podczas gdy projektant pakietów jest wyłączony, te elementy i funkcje projektu nie są spakowane.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowany plik manifestu poprzez wyłączenie projektanta

1. W **projektancie pakietów** wybierz kartę **manifest** .

2. Rozwiń węzeł **Opcje edycji** , wybierz opcję **Zastąp wygenerowany plik XML i edytuj manifest w edytorze XML** , a następnie wybierz przycisk **tak** .

     Szablon zostanie zaktualizowany przy użyciu bieżącego spakowanego pliku manifestu.

## <a name="enable-the-package-designer"></a>Włączanie projektanta pakietów
 Można ponownie włączyć projektanta pakietów, aby dostosować plik *manifest.xml* .

#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć projektanta

1. W **projektancie pakietów** wybierz pozycję **Odrzuć edycje manifestu i ponownie włącz link projektanta** , a następnie wybierz przycisk **tak** .

     Szablon jest odświeżany oryginalnym tekstem i wszelkie zmiany wprowadzone w pliku XML zostaną utracone.

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
