---
title: Udostępnianie klas między językami DSL za pomocą biblioteki DSL
description: Dowiedz się, że w Visual Studio SDK wizualizacji i modelowania można utworzyć niekompletną definicję DSL, która można zaimportować do innego DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3729e4f386ec5a21c8f30ee3f0df6e7ffa8d891
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385503"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Udostępnianie klas między językami DSL za pomocą biblioteki DSL
W Visual Studio SDK wizualizacji i modelowania można utworzyć niekompletną definicję DSL, która można zaimportować do innego dsl. Pozwala to na czynnikowe typowe części podobnych modeli.

## <a name="creating-and-using-dsl-libraries"></a>Tworzenie i używanie bibliotek DSL

#### <a name="to-create-a-dsl-library"></a>Aby utworzyć bibliotekę DSL

1. Utwórz nowy projekt DSL i wybierz szablon rozwiązania biblioteki DSL.

     Zostanie utworzony pojedynczy projekt DSL z pustym modelem.

2. Można dodawać klasy domeny, relacje, kształty i tak dalej.

     Elementy w bibliotece nie muszą tworzyć pojedynczego drzewa osadzania.

     Aby zdefiniować relację, z których mogą korzystać importerzy, utwórz dwie klasy domen i utwórz relację między nimi.

     Rozważ ustawienie **modyfikatora dziedziczenia** klas domeny na `Abstract` .

3. W eksploratorze DSL można dodawać elementy, takie jak konstruktory połączeń.

4. Możesz dodać dostosowania, które wymagają dodatkowego kodu, takie jak ograniczenia walidacji.

5. Kliknij **pozycję Przekształć wszystkie szablony.**

6. Skompiluj projekt.

7. Podczas dystrybucji DSL dla innych osób do użycia, należy podać zarówno skompilowany zestaw (DLL) i plik `DslDefinition.dsl` . Skompilowany zestaw można znaleźć w folderze w folderze `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Aby zaimportować bibliotekę DSL

1. W innej definicji DSL w **Eksploratorze DSL** kliknij prawym przyciskiem myszy klasę główną DSL, a następnie kliknij polecenie Dodaj **nowy import DslLibrary.**

2. W okno Właściwości ustaw **ścieżkę pliku** biblioteki. Można użyć ścieżki względnej lub bezwzględnej.

    Zaimportowana biblioteka jest wyświetlana w Eksploratorze DSL w trybie tylko do odczytu.

3. Zaimportowanych klas można używać jako klas bazowych. Utwórz klasę domeny w importując DSL, a w  okno Właściwości ustaw klasę bazową na zaimportowaną klasę.

4. Kliknij pozycję Przekształć wszystkie szablony.

5. Dodaj do projektu DSL odwołanie do zestawu (DLL), który został sbudowaną przez projekt biblioteki DSL.

6. Skompiluj rozwiązanie.

   Biblioteka DSL może importować inne biblioteki. Podczas importowania biblioteki jej importy są również automatycznie wyświetlane w eksploratorze DSL.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
