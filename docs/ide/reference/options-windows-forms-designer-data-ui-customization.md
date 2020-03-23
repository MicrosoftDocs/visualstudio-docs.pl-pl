---
title: Opcje, Projektant formularzy systemu Windows, Dostosowywanie interfejsu użytkownika danych
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114691"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Okno dialogowe Opcje: Dostosowanie interfejsu użytkownika > programu Windows Forms Designer >

To okno dialogowe określa, które formanty są wyświetlane na liście dostępnych formantów dla elementów w oknie Źródła danych. Aby ją otworzyć, wybierz pozycję **Opcje narzędzi** > **Options**, a następnie wybierz pozycję**Dostosowanie interfejsu użytkownika danych**programu Windows Forms **Designer** > Data .

Formant można wybrać z elementu w oknie Źródła danych przed przeciągnięciem go do formularza w aplikacji Windows Forms. Dostępne formanty są określane przez typ danych elementu. Każdy typ danych ma listę prawidłowych skojarzonych formantów zdefiniowanych w tym oknie dialogowym, w tym formant domyślny. Podczas przeciągania elementu z okna Źródła danych do formularza bez wybierania formantu domyślny formant dla typu danych wybranego elementu jest dodawany do formularza.

Dostosuj listę skojarzonych formantów, zaznaczając i czyszcząc pola wyboru dostępnych formantów dla każdego typu danych. Aby dodać formant do listy, należy dodać formant, który implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute> atrybut lub <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> powiązanie danych do przybornika. Formant pojawi się na liście formantów dla typu danych. Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie kontrolek niestandardowych do okna Źródła danych](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Typ danych

Wyświetla listę typów, z którymi można skojarzyć formanty. Tabele są reprezentowane jako typ `[List]` danych. Kolumny są reprezentowane jako rzeczywisty typ danych kolumny w podstawowym magazynie danych.

## <a name="associated-controls"></a>Skojarzone formanty

Wyświetla listę formantów skojarzonych z wybranym typem danych. Zaznacz lub wyczyść pole wyboru obok formantu, aby skojarzyć lub usunąć skojarzenie. Wybrane formanty są wyświetlane w oknie Źródła danych dla kolumny bazy danych powiązanej ze skojarzonym typem danych.

## <a name="set-default"></a>Ustaw Domyślne

Przypisuje wybrany typ formantu jako domyślny dla wybranego typu danych. Formant domyślny jest wyświetlany jako pierwsze zaznaczenie w menu skrótów dla kolumny bazy danych w oknie Źródła danych. Podczas przeciągania elementu z okna Źródła danych do formularza bez wybierania formantu domyślny formant dla typu danych wybranego elementu jest dodawany do formularza.

Tylko jeden typ formantu można przypisać jako domyślny dla typu danych.

## <a name="clear-default"></a>Wyczyść domyślne

Usuwa oznaczenie formantu jako domyślne dla wybranego typu danych. Jeśli dla wybranego typu danych nie `[None]` ma wartości domyślnej, jest wyświetlany jako pierwsze zaznaczenie w menu skrótów dla kolumny bazy danych tego typu.
