---
title: Opcje, Edytor tekstu, HTML (Formularze sieci Web), Walidacja
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568285"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opcje, Edytor tekstu, HTML (Formularze sieci Web), Walidacja

Na stronie opcje **sprawdzania poprawności** można ustawić preferencje, w jaki sposób Edytor HTML sprawdza składnię znaczników HTML w dokumencie. Aby uzyskać dostęp do tej strony, na pasku menu wybierz **Tools**  >  **Opcje**narzędzia, a następnie rozwiń pozycję **Edytor tekstu**  >  **HTML (Formularze sieci Web)**  >  **Walidacja**.

## <a name="validation"></a>Walidacja

- **Użyj DOCTYPE do wykrywania schematu walidacji**

   Schemat określa, które elementy, atrybuty i wielkie litery są prawidłowe w tym schemacie. Określa również Tagi i atrybuty, które są dostępne w technologii IntelliSense.

   Wybierz tę opcję, jeśli chcesz, aby program Visual Studio korzystał z zawartości< strony ** ! Deklaracja>DOCTYPE ** i element **HTML** , aby określić schemat. Na przykład jeśli wybierzesz tę opcję, a strona zawiera deklarację `<!DOCTYPE html>` , program Visual Studio używa schematu HTML5. Jeśli jednak tag **HTML** ma atrybut **xmlns** , na przykład `<html xmlns="http://www.w3.org/1999/xhtml">` , program Visual Studio używa schematu XHTML5.

- **Obiekt docelowy, gdy nie znaleziono elementu DOCTYPE**

   Wybierz schemat do sprawdzenia, gdy nie ma **<! Deklaracja>DOCTYPE ** na stronie.

  - **Pokaż błędy**

     Zaznacz to pole wyboru, aby włączyć walidację. Jeśli pole wyboru nie jest zaznaczone, Edytor nie oznacza błędów walidacji.

     Pozostałe pola wyboru pozwalają dostosować walidację przez określenie poszczególnych typów błędów, które mają być oznaczone przez Edytor.

     > [!NOTE]
     > Niektóre schematy nie oferują opcji oznaczania poszczególnych typów błędów. Jeśli na przykład wybierzesz **XHTML 1,1** jako schemat docelowy, wszystkie pola wyboru są wyłączone. W tym przypadku wszystkie typy błędów są oznaczane jako zaznaczone.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
