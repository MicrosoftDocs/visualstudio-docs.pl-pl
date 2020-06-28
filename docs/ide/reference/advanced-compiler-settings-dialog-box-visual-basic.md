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
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0c0e6e9d41bb1d4bd7446bb77306ca5a4551906f
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419110"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe

Za pomocą okna dialogowego **Ustawienia AdvancedCompiler** **projektanta projektu** można określić zaawansowane właściwości kompilacji — konfiguracja. To okno dialogowe dotyczy tylko projektów Visual Basic.

## <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W **Eksplorator rozwiązań**wybierz węzeł projektu (nie węzeł **rozwiązania** ).

2. W menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **kompilacja** .

3. Na [stronie kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)wybierz **konfigurację** i **platformę**. W uproszczonych konfiguracjach kompilacji listy **konfiguracji** i **platformy** nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [How to: Set Debug and Release Configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Kliknij pozycję **Zaawansowane opcje kompilacji**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optymalizacje

Poniższe opcje określają optymalizacje, które w niektórych przypadkach sprawiają, że plik programu jest mniejszy, szybsze działanie programu lub przyspieszenie procesu kompilacji.

**Usuń sprawdzanie przepełnienia liczby całkowitej**

To pole wyboru jest domyślnie wyczyszczone, aby włączyć sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli zaznaczysz to pole wyboru, obliczenia liczby całkowitej mogą być szybsze. Jeśli jednak usuniesz sprawdzanie przeciążenia i przepełnienie pojemności typu danych, nieprawidłowe wyniki mogą być przechowywane bez zgłaszania błędu.

Jeśli sprawdzane są warunki przepełnienia, a operacja całkowita przekracza przepływ, <xref:System.OverflowException> zostanie zgłoszony wyjątek. Jeśli warunki przepełnienia nie są zaznaczone, operacje typu Integer przekraczają wyjątek.

**Włącz optymalizacje**

To pole wyboru jest domyślnie wyczyszczone, aby wyłączyć optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Optymalizacje kompilatora sprawiają, że plik wyjściowy jest mniejszy, szybszy i bardziej wydajny. Jednakże, ponieważ optymalizacje powodują ponowne rozmieszczanie kodu w pliku wyjściowym, optymalizacje kompilatora mogą utrudniać debugowanie.

 **Adres podstawowy biblioteki DLL**

To pole tekstowe wyświetla domyślny adres bazy DLL w formacie szesnastkowym. W obszarze Biblioteka klas i projekty bibliotek formantów można użyć tego pola tekstowego, aby określić adres podstawowy, który ma być używany podczas tworzenia biblioteki DLL.

 **Generuj informacje o debugowaniu**

Z listy wybierz opcję **Brak**, **pełna**lub **PDB** . **Brak** określa, że nie są generowane żadne informacje debugowania. **Pełna** określa, że mają zostać wygenerowane pełne informacje o debugowaniu, a **PDB-tylko** określa, że powinny być generowane tylko informacje debugowania PDB. Wartość domyślna tej opcji jest **pełna**.

## <a name="compilation-constants"></a>Stałe kompilacji

Stałe kompilacji warunkowej mają efekt podobny do tego w przypadku używania dyrektywy preprocesora [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) w pliku źródłowym, z wyjątkiem tego, że stałe są zdefiniowane i mają zastosowanie do wszystkich plików w projekcie. Możesz użyć stałych kompilacji warunkowej razem z [#If... Następnie... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) dyrektywa do kompilowania plików źródłowych warunkowo. Zobacz [Kompilacja warunkowa](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Zdefiniuj stałą DEBUG**

To pole wyboru jest domyślnie zaznaczone, co oznacza, że jest ustawiona stała debugowania.

 **Zdefiniuj stałą TRACE**

To pole wyboru jest domyślnie zaznaczone, co oznacza, że jest ustawiona stała śledzenia.

 **Stałe niestandardowe**

Wprowadź dowolne niestandardowe stałe dla aplikacji w tym polu tekstowym. Wpisy powinny być rozdzielane przecinkami, przy użyciu tej formy: **Name1 = "wartość1", NAME2 = "wartość2", nazwa3 = "wartość3"**.

## <a name="other-settings"></a>Inne ustawienia

**Generuj zestawy serializacji**

To ustawienie określa, czy kompilator ma tworzyć zestawy serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania, <xref:System.Xml.Serialization.XmlSerializer> Jeśli użyto tej klasy do serializacji typów w kodzie. Wartość domyślna tej opcji to **Auto.** **Automatycznie** określa, że zestawy serializacji mają być generowane tylko wtedy, gdy zostały użyte <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do formatu XML. **Wyłączone** określa, że zestawy serializacji nigdy nie są generowane, bez względu na to, czy kod używa <xref:System.Xml.Serialization.XmlSerializer> . **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji mają nazwę `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Zobacz też

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
