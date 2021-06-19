---
title: Eksportowanie i zapisywanie map kodu
description: Dowiedz się, jak zapisywać mapy kodu w Visual Studio projektu, jako obrazu lub jako plik XPS.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e58e06c48ed9fa3a9d459c6c615abae4d4b4823f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385685"
---
# <a name="share-code-maps"></a>Udostępnianie map kodu

Mapy kodu można zapisać jako część projektu Visual Studio jako obraz lub jako plik XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Udostępnianie mapy kodu innym użytkownikom Visual Studio

Użyj menu **Plik,** aby zapisać mapę.

-lub-

Aby zapisać mapę w ramach określonego projektu, na pasku narzędzi mapy wybierz pozycję **Udostępnij** przenieś  >  **\<CodeMapName> plik dgml** do pliku , a następnie wybierz projekt, w którym chcesz zapisać mapę.

![Przenoszenie mapy do innego projektu](../modeling/media/codemapsmovemapmenu.png)

Visual Studio mapę jako plik *.dgml,* który można udostępnić innym użytkownikom Visual Studio Enterprise i Visual Studio Professional.

> [!NOTE]
> Przed udostępnieniem mapy osobom, które używają usługi Visual Studio Professional, pamiętaj o rozwinięciu wszystkich grup, pokazaniu ukrytych węzłów i linków między grupami oraz pobraniu wszystkich usuniętych węzłów, które mają być wyświetlane na mapie innym osobom. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.
>
> Następujący błąd może wystąpić podczas zapisywania mapy, która znajduje się w projekcie modelowania lub została skopiowana z projektu modelowania do innej lokalizacji:
>
> "Nie można *zapisać nazwy pliku* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.
>
> Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, utwórz mapę poza projektem modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.

## <a name="export-a-code-map-as-an-image"></a>Eksportowanie mapy kodu jako obrazu

Podczas eksportowania mapy kodu jako obrazu można skopiować ją do innych aplikacji, takich jak Microsoft Word lub PowerPoint.

1. Na pasku narzędzi mapy kodu wybierz pozycję **Udostępnij** wiadomość  >  **e-mail jako obraz lub** Kopiuj **obraz.**

2. Wklej obraz do innej aplikacji.

## <a name="export-the-map-as-an-xps-file"></a>Eksportowanie mapy jako pliku XPS

Podczas eksportowania mapy kodu jako pliku XPS można ją zobaczyć w widokach przeglądarki XML lub XAML, takich jak Internet Explorer.

1. Na pasku narzędzi mapy kodu wybierz pozycję **Udostępnij** pocztę e-mail jako przenośny plik  >  **XPS** lub **zapisz jako przenośny plik XPS.**

2. Przejdź do miejsca, w którym chcesz zapisać plik.

3. Nadaj mapie kodu nazwę . Upewnij się, że **pole Zapisz jako typ** jest ustawione na wartość Pliki **XPS \* (xps).** Wybierz polecenie **Zapisz**.

## <a name="see-also"></a>Zobacz też

- [Mapowanie zależności za pomocą map kodu](../modeling/map-dependencies-across-your-solutions.md)
