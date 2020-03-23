---
title: 'Porady: eksport cieniowania'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a3aec047238786a60b1261415acccfed521695
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589438"
---
# <a name="how-to-export-a-shader"></a>Instrukcje: eksportowanie cieniowania

W tym artykule pokazano, jak za pomocą **Projektanta modułu cieniującego** wyeksportować moduł cieniujący reżyserii języka cieniowania wykresu (DGSL), aby można było go używać w aplikacji.

## <a name="export-a-shader"></a>Eksportowanie cieniowania

Po utworzeniu modułu cieniującego przy użyciu Projektanta modułu cieniującego i przed użyciem go w aplikacji należy wyeksportować go w formacie zrozumiałym dla interfejsu API grafiki. Moduł cieniujący można eksportować na różne sposoby, aby zaspokoić różne potrzeby.

1. W programie Visual Studio otwórz plik **programu Visual Shader Graph (dgsl).**

     Jeśli nie masz pliku **Visual Shader Graph (dgsl)** do otwarcia, utwórz go zgodnie z opisem w jak opisano w [trybie: Tworzenie podstawowego modułu cieniującego kolorów](../designers/how-to-create-a-basic-color-shader.md).

2. Na **pasku narzędzi Projektanta modułów cieniujących** wybierz pozycję **Eksport zaawansowanego** > **eksportu** > **jako**. Zostanie wyświetlone okno dialogowe **Eksportuj moduł cieniujący.**

3. Z listy rozwijanej **Zapisz jako typ** wybierz format, który chcesz wyeksportować.

     Oto formaty, które można wybrać:

     **Moduł cieniujący pikseli\*HLSL ( .hlsl)** Eksportuje moduł cieniujący jako kod źródłowy języka cieniowania wysokiego poziomu (HLSL). Ta opcja umożliwia późniejsze zmodyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawki kodu na podstawie problemów użytkownika końcowego, ale także ułatwia użytkownikowi modyfikowanie modułu cieniującego w niepożądany sposób — na przykład w celu uzyskania nieuczciwej przewagi w konkurencyjnej grze. Może to również zwiększyć czas ładowania modułu cieniującego.

     **Skompilowany moduł\*cieniujący pikseli ( .cso)** Eksportuje moduł cieniujący jako bajtowy HLSL. Ta opcja umożliwia późniejsze zmodyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawki kodu na podstawie problemów użytkownika końcowego, ale ponieważ moduł cieniujący jest wstępnie skompilowany, nie ponosi dodatkowych nakładów pracy po załadowaniu modułu cieniującego przez aplikację. Wystarczająco wykwalifikowani użytkownicy mogą nadal modyfikować moduł cieniujący w niepożądany sposób, ale kompilowanie modułu cieniującego znacznie utrudnia to.

     **Nagłówek języka C++ (\*.h)** Eksportuje moduł cieniujący jako nagłówek w stylu C, który definiuje tablicę bajtów zawierającą kod bajtowy HLSL. Ta opcja może uczynić bardziej czasochłonne debugowanie i poprawki kodu na podstawie problemów użytkownika końcowego, ponieważ aplikacja musi być ponownie skompilowany, aby przetestować poprawkę. Jednak ponieważ ta opcja utrudnia, choć nie niemożliwe, zmodyfikować moduł cieniujący po jego wdrożeniu w aplikacji, przedstawia największą trudność dla użytkownika, który chce zmodyfikować moduł cieniujący w niepożądany sposób.

4. W polu kombi **Nazwa pliku** określ nazwę eksportowanego modułu cieniującego, a następnie wybierz przycisk **Zapisz.**

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
