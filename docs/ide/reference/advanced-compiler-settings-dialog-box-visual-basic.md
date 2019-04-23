---
title: Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8aec1862424be0182e99285ac3772cc9c4bb19f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086692"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe

Użyj **ustawienia AdvancedCompiler** okna dialogowego **projektanta projektu** określić najbardziej zaawansowane właściwości konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic.

## <a name="to-access-this-dialog-box"></a>Dostęp do tego okna dialogowego

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).

2. Na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawi się, kliknij przycisk **skompilować** kartę.

3. Na [strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), wybierz opcję **konfiguracji** i **platformy**. W uproszczonych konfiguracjach kompilacji **konfiguracji** i **platformy** listy nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [jak: Zestaw debugowania i zwalniania konfiguracji](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Kliknij przycisk **zaawansowane opcje kompilacji**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optymalizacje

 Następujące opcje określają optymalizacje, które można w niektórych przypadkach zmniejszyć pliku programu, napisać program, który działają szybciej i przyspieszyć proces kompilacji.

**Usuń sprawdzenia przepełnienia liczb całkowitych**

To pole wyboru jest wyczyszczone, domyślnie, aby włączyć sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli wybierzesz to pole wyboru, obliczeń na liczbach całkowitych może przebiegać szybciej. Jednak usunięcie przepełnienie sprawdzanie i dane typu pojemności przepełnienie niepoprawne wyniki mogą być przechowywane bez błędu są zgłaszane.

Jeśli przepełnienie warunki są sprawdzane i przepełnienia liczby całkowitej operacji, <xref:System.OverflowException> wyjątku. Jeśli przepełnienie warunki nie są zaznaczone, przepełnienia operacji całkowitą nie zgłasza wyjątku.

**Włącz optymalizacje**

To pole wyboru jest wyczyszczone, domyślnie, aby wyłączyć optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Plik wyjściowy był optymalizacje kompilatora, mniejszy, szybszy i bardziej wydajne. Jednak ponieważ optymalizacje kodu zmiana położenia w pliku wyjściowym, optymalizacje kompilatora może utrudnić debugowanie.

 **Adres podstawowy DLL**

 To pole tekstowe wyświetla domyślny adres podstawowy DLL w formacie szesnastkowym. W projektach biblioteki klas i Biblioteka kontrolek można użyć tego pola tekstowego, aby określić adres podstawowy, który będzie używany podczas tworzenia biblioteki DLL.

 **Generuj informacje o debugowaniu**

 Wybierz **Brak**, **pełne**, lub **tylko do pdb** z listy. **Brak** Określa, że żadne informacje debugowania będą generowane. **Pełne** Określa, że pełne informacje debugowania będą generowane, i **tylko do pdb** Określa, czy powinny być generowane tylko wtedy PDB, informacje o debugowaniu. Wartość domyślna tej opcji to **pełne**.

## <a name="compilation-constants"></a>Stałe kompilacji

Stałe kompilacji warunkowej ma efekt jest podobny do korzystania z [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) dyrektywy preprocesora w źródle pliku, z tą różnicą, że stałe zdefiniowane są publiczne i zastosować do wszystkich plików w projekcie. Możesz użyć stałe kompilacji warunkowej, wraz z [#If... Then... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) dyrektywy, aby warunkowo skompilować pliki źródłowe. Zobacz [kompilacji warunkowej](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Zdefiniuj stałą DEBUG**

 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą DEBUG.

 **Zdefiniuj stałą TRACE**

 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą TRACE.

 **Stałe niestandardowe**

 Wprowadź wszelkie stałe niestandardowych dla aplikacji w taki sposób, w tym polu tekstowym. Wpisy powinny być rozdzielone przecinkami, za pomocą tego formularza: **Nazwa1 = "Wartość1," Nazwa2 = "Wartość2", nazwa3 = "Wartość3"**.

## <a name="other-settings"></a>Inne ustawienia

**Generuj zestawy serializacji**

To ustawienie określa, czy kompilator utworzy zestawy serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania klasy <xref:System.Xml.Serialization.XmlSerializer> jeśli używano tej klasy do serializacji typów w kodzie. Wartość domyślna tej opcji to **automatycznie**. **Automatyczne** Określa, że zestawy serializacji będą generowane tylko wtedy, gdy znasz <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do XML. **Wyłącz** Określa, że zestawy serializacji nigdy nie są generowane, niezależnie od tego, czy kod używa <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, że zestawy serializacji zawsze będą generowane. Zestawy serializacji noszą `TypeName`. XmlSerializers.dll.

## <a name="see-also"></a>Zobacz także

- [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)