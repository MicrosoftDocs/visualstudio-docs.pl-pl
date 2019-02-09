---
title: Opcje, Edytor tekstu HTML (formularze sieci Web), sprawdzanie poprawności
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d06674d476dd671f715d2f4c88bdd23852f78687
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970676"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opcje, Edytor tekstu HTML (formularze sieci Web), sprawdzanie poprawności

Użyj **weryfikacji** Strona opcji, aby ustawić preferencje dotyczące sposobu edytora HTML sprawdza składnię kod znaczników HTML w dokumencie. Dostępu do tej strony, na pasku menu wybierz **narzędzia** > **opcje**, a następnie rozwiń węzeł **edytora tekstów** > **HTML (formularze sieci Web)**   >  **Weryfikacji**.

## <a name="validation"></a>Walidacja

- **Użyj doctype do wykrywania schematu walidacji**

   Schemat określa, które elementy, atrybuty i wielkość liter są prawidłowe w tym schemacie. Określa również znaczniki i atrybuty, które są dostępne w technologii IntelliSense.

   Wybierz tę opcję, jeśli chcesz, aby Visual Studio, aby korzystać z zawartości strony **<! DOCTYPE >** deklaracji i **html** element, aby ustalić schemat. Na przykład jeśli wybierzesz tę opcję i na stronie ma deklaracji `<!DOCTYPE html>`, program Visual Studio używa schematu HTML5. Jednak jeśli **html** tag ma **xmlns** atrybutów, takich jak `<html xmlns="http://www.w3.org/1999/xhtml">`, program Visual Studio używa schematu XHTML5.

- **Docelowy element**

   Wybierz schemat na potrzeby sprawdzania poprawności, gdy istnieje nie **<! DOCTYPE >** deklaracji na stronie.

  - **Pokaż błędy**

     Zaznacz pole wyboru, aby włączyć weryfikację. Jeśli pole wyboru nie jest zaznaczone, edytor nie oznaczyć błędy sprawdzania poprawności.

     Pozostałe pola wyboru umożliwiają dostosowanie weryfikacji przez określenie poszczególnych typów błędów, które chcesz oznaczyć w edytorze.

     > [!NOTE]
     > Niektóre schematy nie oferuje opcji, aby oznaczyć poszczególne typy błędów. Na przykład, jeśli wybierzesz **XHTML 1.1** jako schemat docelowy wszystkie pola wyboru opcji są wyłączone. W tym wypadku są oznaczane wszystkie typy błędów.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)