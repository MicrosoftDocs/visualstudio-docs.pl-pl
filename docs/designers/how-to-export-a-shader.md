---
title: 'Porady: eksport cieniowania'
description: Dowiedz się, jak eksportować ukierunkowany program do cieniowania grafu wykresu przy użyciu projektanta programu do cieniowania, aby można było go używać w aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da09feffc4d2f804660f02dbda6055bf59099500
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134305"
---
# <a name="how-to-export-a-shader"></a>Instrukcje: eksportowanie cieniowania

W tym artykule pokazano, jak używać **projektanta cieniowania** do eksportowania programu cieniowania ukierunkowanego języka programu Graph (DGSL), dzięki czemu można go używać w aplikacji.

## <a name="export-a-shader"></a>Eksportowanie cieniowania

Po utworzeniu modułu cieniującego przy użyciu projektanta programu do cieniowania i przed użyciem go w aplikacji należy wyeksportować go w formacie, który rozpoznaje interfejs API grafiki. Program do cieniowania można wyeksportować na różne sposoby, aby zaspokoić różne potrzeby.

1. W programie Visual Studio Otwórz plik **grafu programu Visual Shader (. dgsl)** .

     Jeśli nie masz pliku **grafu programu Visual Shader (. dgsl)** do otwarcia, utwórz go zgodnie z opisem w temacie [How to: Create a Basic Color Shader](../designers/how-to-create-a-basic-color-shader.md).

2. Na pasku narzędzi **projektanta cieniowania** wybierz pozycję **Zaawansowany**  >  **eksport eksportu**  >  **jako** . Zostanie wyświetlone okno dialogowe Eksportowanie programu do **cieniowania** .

3. Z listy rozwijanej **Zapisz jako typ** wybierz format, który chcesz wyeksportować.

     Oto formaty, które możesz wybrać:

     Program do **cieniowania pikseli HLSL ( \* . HLSL)** eksportuje program do cieniowania jako kod źródłowy języka HLSL (High Level Shader Language). Ta opcja umożliwia późniejsze modyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawianie kodu w oparciu o problemy z użytkownikami końcowymi, ale ułatwia użytkownikowi modyfikowanie modułu cieniującego na niechcianych sposobach — na przykład w celu uzyskania nieuczciwej korzyści w ramach konkurencyjnej gry. Może również zwiększyć czas ładowania cieniowania.

     **Skompilowany program do cieniowania pikseli ( \* . CSO)** eksportuje program do cieniowania jako HLSL kod bajtowy. Ta opcja umożliwia późniejsze modyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawianie kodu w oparciu o problemy z użytkownikami końcowymi, ale ponieważ program do cieniowania jest wstępnie skompilowany, nie wiąże się z dodatkowym obciążeniem środowiska uruchomieniowego, gdy program do cieniowania jest ładowany przez aplikację. Wystarczająco wykwalifikowanych użytkowników nadal można modyfikować cieniowanie na niechcianych sposobach, ale Kompilowanie cieniowania znacznie trudniejsze.

     **Nagłówek C++ ( \* . h)** eksportuje program do cieniowania jako nagłówek w stylu C, który definiuje tablicę bajtową zawierającą kod bajtowy HLSL. Ta opcja może zwiększyć czasochłonną funkcję debugowania i poprawiania kodu na podstawie problemów z użytkownikami końcowymi, ponieważ należy ponownie skompilować aplikację w celu przetestowania poprawki. Jednak ponieważ ta opcja utrudnia, chociaż nie jest to możliwe, można zmodyfikować program do cieniowania po jego wdrożeniu w aplikacji, co sprawia, że użytkownik chce zmodyfikować cieniowanie w niepożądane sposoby.

4. W polu kombi **Nazwa pliku** Podaj nazwę wyeksportowanego programu do cieniowania, a następnie wybierz przycisk **Zapisz** .

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie cieniowania koloru podstawowego](../designers/how-to-create-a-basic-color-shader.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
