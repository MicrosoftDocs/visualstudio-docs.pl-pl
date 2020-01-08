---
title: Opcje formatowania edytora U-SQL
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 200ec41a1295178f1127d10053985384a7813158
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568272"
---
# <a name="options-text-editor-u-sql-formatting"></a>Opcje, Edytor tekstu, U-SQL, formatowanie

Na stronie opcje **formatowania** można ustawić opcje formatowania kodu w edytorze kodu. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję **narzędzia** > **Opcje**. W oknie dialogowym **Opcje** wybierz pozycję **Edytor tekstu** > formatowanie **U-SQL** > .

## <a name="general-page"></a>Strona Ogólne

### <a name="general-settings"></a>Ustawienia ogólne

Te ustawienia mają wpływ na to, *kiedy* Edytor kodu stosuje opcje formatowania do kodu.

- **Automatycznie Formatuj ukończoną instrukcję przy wprowadzaniu średnika**

   Po wybraniu formatuje instrukcje w przypadku wybrania klucza średnika zgodnie z opcjami formatowania wybranymi dla edytora.

- **Automatycznie Formatuj przy wklejaniu**

   Gdy ta opcja jest zaznaczona, formatuje tekst wklejony do edytora, aby dopasować opcje formatowania wybrane dla edytora.

## <a name="preview-windows"></a>Okna wersji zapoznawczej

Podstrony **wcięcia**, **nowe wiersze**i **odstępy** są wyświetlane u dołu okna podglądu. Okno podglądu pokazuje efekt każdej opcji. Aby użyć okna podglądu, wybierz opcję formatowania. Okno podglądu zawiera przykład wybranej opcji. Gdy zmienisz ustawienie, zaznaczając pole wyboru, okno podglądu zostanie zaktualizowane, aby pokazać efekt nowego ustawienia.

### <a name="indentation-remarks"></a>Uwagi dotyczące wcięć

Opcje wcięć na stronach **kart** dla każdego języka określają, gdzie Edytor kodu umieszcza kursor po naciśnięciu klawisza **Enter** na końcu wiersza. Opcje wcięć w obszarze **Formatowanie** stosuje się, gdy kod jest formatowany automatycznie, na przykład:

- Podczas wklejania kodu do pliku, gdy jest zaznaczone **Automatyczne formatowanie przy wklejaniu**
- Gdy format jest formatowany ręcznie

## <a name="see-also"></a>Zobacz także

- [Okno dialogowe Ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md)
