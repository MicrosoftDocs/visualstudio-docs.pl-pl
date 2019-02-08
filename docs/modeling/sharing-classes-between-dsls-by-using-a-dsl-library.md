---
title: Udostępnianie klas między językami DSL za pomocą biblioteki DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 640936fbe0218bbb8e6d710547c39a4bfbf0bc9e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918120"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Udostępnianie klas między językami DSL za pomocą biblioteki DSL
W Visual Studio Visualization i Modeling SDK można utworzyć niekompletne definicji DSL, który można zaimportować do innego języka DSL. Dzięki temu można wziąć pod uwagę części wspólnej podobne modeli.

## <a name="creating-and-using-dsl-libraries"></a>Tworzenie i używanie biblioteki DSL

#### <a name="to-create-a-dsl-library"></a>Aby utworzyć biblioteki DSL

1.  Tworzenie nowego projektu DSL, a następnie wybierz szablon rozwiązania bibliotekę DSL.

     Do tego pojedynczego projektu DSL zostanie utworzony przy użyciu modelu puste.

2.  Można dodać klasy domeny, relacje, kształty i tak dalej.

     Elementy w bibliotece nie trzeba utworzyć pojedynczy drzewo osadzania.

     Aby zdefiniować relacji importers można użyć, Utwórz dwoma klasami domeny i tworzenie relacji między nimi.

     Rozważ ustawienie **modyfikator dziedziczenia** klas domeny na potrzeby `Abstract`.

3.  Możesz dodać elementy, które określają w Eksplorator DSL, takich jak konstruktory połączeń.

4.  Można dodać dostosowania, które wymagają dodatkowego kodu, takie jak ograniczenia sprawdzania poprawności.

5.  Kliknij przycisk **Transformuj wszystkie szablony**.

6.  Skompiluj projekt.

7.  Podczas dystrybucji DSL, aby inne osoby mogły używać należy podać zarówno w skompilowanym zestawie (DLL), jak i plik `DslDefinition.dsl`. Skompilowanego zestawu można znaleźć w folderze w `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Aby zaimportować biblioteki DSL

1. W innej definicji DSL w **Eksplorator DSL**, kliknij prawym przyciskiem myszy klasę głównego język DSL, a następnie kliknij przycisk **Dodaj nowy element DslLibrary Import**.

2. W oknie właściwości ustaw **ścieżka pliku** biblioteki. Można użyć względna lub bezwzględna.

    Zaimportowanej biblioteki pojawia się w Eksplorator DSL w trybie tylko do odczytu.

3. Zaimportowane klasy można użyć jako klasy bazowej. Utwórz klasę domeny w importowania DSL, a w oknie właściwości ustaw oknie **klasa bazowa** do zaimportowanej klasy.

4. Kliknij przycisk Przekształć wszystkie szablony.

5. Dodaj do projektu DSL odwołanie do zestawu (DLL), który został zbudowany przez projekt biblioteki DSL.

6. Skompiluj rozwiązanie.

   Biblioteka DSL można zaimportować innych bibliotek. Podczas importowania biblioteki jego importów również automatycznie są wyświetlane w Eksploratorze DSL.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
