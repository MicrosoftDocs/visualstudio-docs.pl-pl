---
title: Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ebc2da5e71dbdee13df4cf658f3681804879f58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596934"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe

Użyj okna dialogowego **Zaawansowane ustawienia kompilatora** **projektanta projektu,** aby określić właściwości zaawansowanej konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko projektów języka Visual Basic.

## <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu (nie węzeł **Rozwiązanie).**

2. W menu **Projekt** kliknij polecenie **Właściwości**. Po wyświetleniu **projektanta projektu** kliknij kartę **Kompilacja.**

3. Na [stronie Kompilacja projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)wybierz **opcję Konfiguracja** i **platforma**. W uproszczonych konfiguracjach kompilacji nie są wyświetlane listy **Konfiguracja** i **Platforma.** Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie konfiguracji debugowania i zwalniania](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Kliknij **pozycję Opcje kompilacji zaawansowanej**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optymalizacje

Następujące opcje określają optymalizacje, które w niektórych przypadkach mogą zmniejszyć plik programu, przyspieszyć uruchamianie programu lub przyspieszyć proces kompilacji.

**Usuwanie kontroli przepełnienia liczby całkowitej**

To pole wyboru jest domyślnie wyczyszczone, aby włączyć sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli zaznaczysz to pole wyboru, obliczenia liczby całkowitej mogą być szybsze. Jednak w przypadku usunięcia kontroli przepełnienia i przepełnienie pojemności typu danych, niepoprawne wyniki mogą być przechowywane bez wywoływania błędu.

Jeśli warunki przepełnienia są sprawdzane i operacja całkowita <xref:System.OverflowException> przepełnienia, wyjątek. Jeśli warunki przepełnienia nie są sprawdzane, przepełnienia operacji całkowitej nie zgłaszają wyjątku.

**Włącz optymalizacje**

To pole wyboru jest domyślnie wyczyszczone, aby wyłączyć optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Optymalizacje kompilatora sprawiają, że plik wyjściowy jest mniejszy, szybszy i wydajniejszy. Jednak ponieważ optymalizacje powodują zmianę rozmieszczenia kodu w pliku wyjściowym, optymalizacje kompilatora może utrudnić debugowanie.

 **Adres podstawowy biblioteki DLL**

W tym polu tekstowym jest wyświetlany domyślny adres bazowy biblioteki DLL w formacie szesnastowym. W projektach biblioteki klas i biblioteki sterowania można użyć tego pola tekstowego, aby określić adres podstawowy, który ma być używany podczas tworzenia biblioteki DLL.

 **Generowanie informacji o debugowaniu**

Z listy wybierz **opcję Brak,** **Pełna**lub **PDB.** **Brak** określa, że nie można wygenerować żadnych informacji debugowania. **Full** określa, że pełne informacje debugowania mają być generowane, a **pdb-only** określa, że tylko informacje debugowania PDB powinny być generowane. Wartością domyślną dla tej opcji jest **Pełna**.

## <a name="compilation-constants"></a>Stałe kompilacji

Stałe kompilacji warunkowej mają działanie podobne do tego, że przy użyciu dyrektywy preprocesora [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) w pliku źródłowym, z tą różnicą, że zdefiniowane stałe są publiczne i mają zastosowanie do wszystkich plików w projekcie. Można użyć stałych kompilacji warunkowej wraz z [#If... Następnie ... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) dyrektywy do kompilacji plików źródłowych warunkowo. Zobacz [Kompilacja warunkowa](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Zdefiniuj stałą DEBUG**

Domyślnie to pole wyboru jest zaznaczone, określając, że ustawiona jest stała DEBUG.

 **Zdefiniuj stałą TRACE**

Domyślnie to pole wyboru jest zaznaczone, określając, że ustawiono stałą TRACE.

 **Stałe niestandardowe**

Wprowadź wszystkie stałe niestandardowe dla aplikacji w tym polu tekstowym. Wpisy powinny być rozdzielane przecinkami, używając tego formularza: **Name1="Value1,"Name2="Value2,"Name3="Value3"**.

## <a name="other-settings"></a>Inne ustawienia

**Generowanie zestawów serializacji**

To ustawienie określa, czy kompilator utworzy zestawy serializacji XML. Zestawy serializacji można poprawić wydajność <xref:System.Xml.Serialization.XmlSerializer> uruchamiania, jeśli używasz tej klasy do serializacji typów w kodzie. Wartością domyślną dla tej opcji jest **Auto**. **Auto** określa, że zestawy serializacji są generowane <xref:System.Xml.Serialization.XmlSerializer> tylko wtedy, gdy użyto do kodowania typów w kodzie do XML. **Off** określa, że zestawy serializacji nigdy nie są generowane, <xref:System.Xml.Serialization.XmlSerializer>niezależnie od tego, czy używany jest kod. **Na** określa, że zestawy serializacji zawsze być generowane. Zestawy serializacji mają `TypeName`nazwy . XmlSerializers.dll.

## <a name="see-also"></a>Zobacz też

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
