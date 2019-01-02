---
title: Wyeksportować i zapisać map kodu
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: c80c99effebab8d2dffa53621af8f7c60bcad629
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900811"
---
# <a name="share-code-maps"></a>Udostępnianie map kodu

Mapy kodu można zapisać jako część projektu programu Visual Studio, jako obraz lub jako plik XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Udostępniać innym użytkownikom programu Visual Studio mapy kodu

Użyj **pliku** menu, aby zapisać na mapie.

—lub—

Aby zapisać mapy jako część określonego projektu, na pasku narzędzi mapy, wybierz **udziału** > **przenieść \<CodeMapName > .dgml do**, a następnie wybierz projekt, w którym chcesz zapisać Mapa.

![Przenieś mapę do innego projektu](../modeling/media/codemapsmovemapmenu.png)

Program Visual Studio zapisuje mapy jako *.dgml* pliku, który można udostępniać innym użytkownikom programu Visual Studio Enterprise i Visual Studio Professional.

> [!NOTE]
> Przed udostępnieniem map użytkownikom korzystającym z programu Visual Studio Professional, pamiętaj Rozwiń wszystkie grupy, Pokaż ukryte węzły i łącza między grupami i Pobierz wszelkie usunięte węzły, które inni mają zobaczyć na mapie. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.
>
> Po zapisaniu mapę, która znajduje się w projekcie modelowania lub został skopiowany z projektu modelowania w inne miejsce, mógł wystąpić następujący błąd:
>
> "Nie można zapisać *fileName* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.
>
> Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, należy utworzyć mapy poza projektem modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.

## <a name="export-a-code-map-as-an-image"></a>Eksportuj mapę kodu jako obraz

Podczas eksportowania mapę kodu jako obraz, skopiuj go do innych aplikacji, takich jak Microsoft Word lub PowerPoint.

1. Na pasku narzędzi mapy kodu Wybierz **udziału** > **poczty E-mail jako obraz** lub **Kopiuj obraz**.

2. Wklej obraz do innej aplikacji.

## <a name="export-the-map-as-an-xps-file"></a>Eksportowanie mapy jako plik XPS

Gdy mapy kodu możesz wyeksportować jako plik XPS, możesz to sprawdzić w XML lub XAML przeglądarki, takich jak Internet Explorer.

1. Na pasku narzędzi mapy kodu Wybierz **udziału** > **wiadomości E-mail jako przenośny dokument XPS** lub **Zapisz jako przenośny dokument XPS**.

2. Przejdź do której chcesz zapisać plik.

3. Nazwa mapy kodu. Upewnij się, że **Zapisz jako typ** pole jest ustawiona na **pliki XPS (\*.xps)**. Wybierz polecenie **Zapisz**.

## <a name="see-also"></a>Zobacz także

- [Mapowanie zależności z mapami kodu](../modeling/map-dependencies-across-your-solutions.md)