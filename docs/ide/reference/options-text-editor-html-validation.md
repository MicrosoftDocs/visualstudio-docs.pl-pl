---
title: Opcje, Edytor tekstu, HTML (formularze sieci Web), Sprawdzanie poprawności
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568285"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opcje, Edytor tekstu, HTML (formularze sieci Web), Sprawdzanie poprawności

Strona Opcje **sprawdzania poprawności** służy do ustawiania preferencji dotyczących sposobu, w jaki edytor HTML sprawdza składnię znaczników HTML w dokumencie. Aby uzyskać dostęp do tej strony, na pasku menu wybierz pozycję**Opcje** **narzędzi** > , a następnie rozwiń pozycję**Sprawdzanie poprawności**HTML **edytora** > **tekstu HTML (Formularze sieci Web).** > 

## <a name="validation"></a>Sprawdzanie poprawności

- **Używanie doctype do wykrywania schematu sprawdzania poprawności**

   Schemat określa, które elementy, atrybuty i wielkość liter są prawidłowe w tym schemacie. Określa również tagi i atrybuty, które są dostępne w IntelliSense.

   Wybierz tę opcję, jeśli chcesz, aby program Visual Studio używał zawartości **< strony! DOCTYPE>** deklaracji i elementu **html** w celu określenia schematu. Na przykład jeśli wybierzesz tę opcję, `<!DOCTYPE html>`a strona ma deklarację, program Visual Studio używa schematu HTML5. Jeśli jednak tag **html** ma atrybut **xmlns,** na przykład `<html xmlns="http://www.w3.org/1999/xhtml">`program Visual Studio używa schematu XHTML5.

- **Cel, gdy nie znaleziono doctype**

   Wybierz schemat, aby sprawdzić poprawność, gdy nie ma **<! DOCTYPE>** deklaracji na stronie.

  - **Pokaż błędy**

     Zaznacz to pole wyboru, aby włączyć sprawdzanie poprawności. Jeśli pole wyboru nie jest zaznaczone, edytor nie oznacza błędów sprawdzania poprawności.

     Inne pola wyboru umożliwiają precyzyjne dostosowywanie sprawdzania poprawności przez określenie poszczególnych typów błędów, które mają oznaczać edytor.

     > [!NOTE]
     > Niektóre schematy nie oferują opcji oznaczania poszczególnych typów błędów. Na przykład jeśli jako schemat docelowy wybierzesz **XHTML 1.1,** wszystkie pola wyboru opcji zostaną wyłączone. W tym przypadku wszystkie typy błędów są oznaczone.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
