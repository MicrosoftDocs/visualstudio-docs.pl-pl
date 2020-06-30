---
title: Udostępnianie klas między językami DSL za pomocą biblioteki DSL
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38496141d6fcdd33f3bf5185c3f50b1bf961d832
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542548"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Udostępnianie klas między językami DSL za pomocą biblioteki DSL
W programie Visual Studio Wizualizacja i Modeling SDK można utworzyć niekompletną definicję DSL, którą można zaimportować do innego modemu DSL. Pozwala to na wspólne części podobnych modeli.

## <a name="creating-and-using-dsl-libraries"></a>Tworzenie i używanie bibliotek DSL

#### <a name="to-create-a-dsl-library"></a>Aby utworzyć bibliotekę DSL

1. Utwórz nowy projekt DSL i wybierz szablon rozwiązania biblioteki DSL.

     Pojedynczy projekt DSL zostanie utworzony z pustym modelem.

2. Można dodać klasy domen, relacje, kształty i tak dalej.

     Elementy w bibliotece nie muszą tworzyć jednego drzewa osadzania.

     Aby zdefiniować relację, która może być używana przez importerów, należy utworzyć dwie klasy domeny i utworzyć relację między nimi.

     Rozważ ustawienie **modyfikatora dziedziczenia** klas domeny na `Abstract` .

3. Można dodawać elementy zdefiniowane w Eksploratorze DSL, takie jak konstruktory połączeń.

4. Można dodać dostosowania wymagające dodatkowego kodu, takie jak ograniczenia walidacji.

5. Kliknij kolejno pozycje **Przekształć wszystkie szablony**.

6. Skompiluj projekt.

7. W przypadku dystrybucji DSL do użytku przez inne osoby należy zapewnić zarówno skompilowany zestaw (DLL), jak i plik `DslDefinition.dsl` . Skompilowany zestaw można znaleźć w folderze`Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Aby zaimportować bibliotekę DSL

1. W innej definicji DSL, w **Eksploratorze DSL**, kliknij prawym przyciskiem myszy klasy głównej DSL, a następnie kliknij pozycję **Dodaj nowy DslLibrary zaimportować**.

2. W okno Właściwości ustaw **ścieżkę pliku** biblioteki. Możesz użyć ścieżki względnej lub bezwzględnej.

    Zaimportowana Biblioteka pojawia się w Eksploratorze DSL w trybie tylko do odczytu.

3. Zaimportowanych klas można użyć jako klas bazowych. Utwórz klasę domeny w imporcie DSL i w okno Właściwości ustaw **klasę bazową** na zaimportowaną klasę.

4. Kliknij kolejno pozycje Przekształć wszystkie szablony.

5. Dodaj do projektu DSL odwołanie do zestawu (DLL), który został skompilowany przez projekt biblioteki DSL.

6. Skompiluj rozwiązanie.

   Biblioteka DSL może importować inne biblioteki. Podczas importowania biblioteki jego Importy są również automatycznie wyświetlane w Eksploratorze DSL.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
