---
title: 'Instrukcje: Eksportowanie cieniowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2225ce416fed4e97e998a50f70a0dc4c25908476
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664472"
---
# <a name="how-to-export-a-shader"></a>Porady: eksport cieniowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia programu do cieniowania programu Graph w celu wyeksportowania bezpośredniego modułu cieniującego grafu języka (DGSL), dzięki któremu można używać go w aplikacji.

 Ten dokument przedstawia następujące działania:

- Eksportowanie cieniowania

## <a name="exporting-a-shader"></a>Eksportowanie cieniowania
 Po utworzeniu modułu cieniującego przy użyciu projektanta programu do cieniowania i przed użyciem go w aplikacji należy wyeksportować go w formacie, który rozpoznaje interfejs API grafiki. Program do cieniowania można wyeksportować na różne sposoby, aby zaspokoić różne potrzeby.

#### <a name="to-export-a-shader"></a>Aby wyeksportować cieniowanie

1. W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz plik **grafu programu Visual Shader (. dgsl)** .

     Jeśli nie masz pliku **grafu programu Visual Shader (. dgsl)** do otwarcia, utwórz go zgodnie z opisem w temacie [How to: Create a Basic Color Shader](../designers/how-to-create-a-basic-color-shader.md).

2. Na pasku narzędzi projektanta programu do **cieniowania** wybierz pozycję **Zaawansowane**, **Eksportuj**, **Eksportuj jako**. Zostanie wyświetlone okno dialogowe Eksportowanie programu do **cieniowania** .

3. Z listy rozwijanej **Zapisz jako typ** wybierz format, który chcesz wyeksportować.

     Oto formaty, które możesz wybrać:

     Program do **cieniowania pikseli HLSL ( \* . HLSL)** eksportuje program do cieniowania jako kod źródłowy języka HLSL (High Level Shader Language). Ta opcja umożliwia późniejsze modyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawianie kodu w oparciu o problemy z użytkownikami końcowymi, ale ułatwia użytkownikowi modyfikowanie modułu cieniującego na niechcianych sposobach — na przykład w celu uzyskania nieuczciwej korzyści w ramach konkurencyjnej gry. Może również zwiększyć czas ładowania cieniowania.

     **Skompilowany program do cieniowania pikseli ( \* . CSO)** eksportuje program do cieniowania jako HLSL kod bajtowy. Ta opcja umożliwia późniejsze modyfikowanie modułu cieniującego, nawet po jego wdrożeniu w aplikacji. Może to ułatwić debugowanie i poprawianie kodu w oparciu o problemy z użytkownikami końcowymi, ale ponieważ program do cieniowania jest wstępnie skompilowany, nie wiąże się z dodatkowym obciążeniem środowiska uruchomieniowego, gdy program do cieniowania jest ładowany przez aplikację. Wystarczająco wykwalifikowanych użytkowników nadal można modyfikować cieniowanie na niechcianych sposobach, ale Kompilowanie cieniowania znacznie trudniejsze.

     **Nagłówek C++ ( \* . h)** eksportuje program do cieniowania jako nagłówek w stylu C, który definiuje tablicę bajtową zawierającą kod bajtowy HLSL. Ta opcja może zwiększyć czasochłonną funkcję debugowania i poprawiania kodu na podstawie problemów z użytkownikami końcowymi, ponieważ należy ponownie skompilować aplikację w celu przetestowania poprawki. Jednak ponieważ ta opcja utrudnia, chociaż nie jest to możliwe, można zmodyfikować program do cieniowania po jego wdrożeniu w aplikacji, co sprawia, że użytkownik chce zmodyfikować cieniowanie w niepożądane sposoby.

4. W polu kombi **Nazwa pliku** Podaj nazwę wyeksportowanego programu do cieniowania, a następnie wybierz przycisk **Zapisz** .

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie podstawowego](../designers/how-to-create-a-basic-color-shader.md) [projektanta cieniowania](../designers/shader-designer.md) kolorów
