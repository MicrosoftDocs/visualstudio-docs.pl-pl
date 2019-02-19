---
title: Zaawansowane ustawienia kompilatora, okno dialogowe (Visual Basic) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c1932f3b9a065115c7977207b0678fbcd44c2e4
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758893"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Użyj **ustawienia AdvancedCompiler** okna dialogowego **projektanta projektu** określić najbardziej zaawansowane właściwości konfiguracji kompilacji projektu. To okno dialogowe dotyczy tylko dla projektów języka Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Dostęp do tego okna dialogowego  
  
1. W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).  
  
2. Na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** pojawi się, kliknij przycisk **skompilować** kartę.  
  
3. Na [strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), wybierz opcję **konfiguracji** i **platformy**. W uproszczonych konfiguracjach kompilacji **konfiguracji** i **platformy** listy nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
4. Kliknij przycisk **zaawansowane opcje kompilacji**.  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="optimizations"></a>Optymalizacje  
 Następujące opcje określają optymalizacje, które można w niektórych przypadkach zmniejszyć pliku programu, napisać program, który działają szybciej i przyspieszyć proces kompilacji.  
  
 **Usuń sprawdzenia przepełnienia liczb całkowitych**  
 Domyślnie to pole wyboru jest wyczyszczone, aby włączyć sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli wybierzesz to pole wyboru, obliczeń na liczbach całkowitych może przebiegać szybciej. Jednak usunięcie przepełnienie sprawdzanie i dane typu pojemności przepełnienie niepoprawne wyniki mogą być przechowywane bez błędu są zgłaszane.  
  
 Jeśli przepełnienie warunki są sprawdzane i przepełnienia liczby całkowitej operacji, <xref:System.OverflowException> wyjątku. Jeśli przepełnienie warunki nie są zaznaczone, przepełnienia operacji liczby całkowitej nie zgłasza wyjątku.  
  
 **Włącz optymalizacje**  
 Domyślnie to pole wyboru jest wyczyszczone w celu Wyłącz optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Plik wyjściowy był optymalizacje kompilatora, mniejszy, szybszy i bardziej wydajne. Jednak ponieważ optymalizacje kodu zmiana położenia w pliku wyjściowym, optymalizacje kompilatora może utrudnić debugowanie.  
  
 **Adres podstawowy DLL**  
 To pole tekstowe wyświetla domyślny adres podstawowy DLL w formacie szesnastkowym. W projektach biblioteki klas i Biblioteka kontrolek można użyć tego pola tekstowego, aby określić adres podstawowy, który będzie używany podczas tworzenia biblioteki DLL.  
  
 **Generuj informacje o debugowaniu**  
 Wybierz **Brak**, **pełne**, lub **tylko do pdb** z listy. **Brak** Określa, że żadne informacje debugowania będą generowane. **Pełne** Określa, że pełne informacje debugowania będą generowane, i **tylko do pdb** Określa, że tylko wtedy PDB informacje debugowania będą generowane. Domyślnie ta opcja jest ustawiona na **pełne**.  
  
## <a name="compilation-constants"></a>Stałe kompilacji  
 Stałe kompilacji warunkowej ma efekt jest podobny do korzystania z [#Const](http://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) dyrektywy preprocesora w źródle pliku, z tą różnicą, że stałe zdefiniowane są publiczne i zastosować do wszystkich plików w projekcie. Możesz użyć stałe kompilacji warunkowej, wraz z [#If... Then... #Else](http://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) dyrektywy, aby warunkowo skompilować pliki źródłowe. Zobacz [kompilacji warunkowej](http://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).  
  
 **Zdefiniuj stałą DEBUG**  
 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą DEBUG.  
  
 **Zdefiniuj stałą TRACE**  
 Domyślnie to pole wyboru jest zaznaczone, określając, że można ustawić stałą TRACE.  
  
 **Stałe niestandardowe**  
 Wprowadź wszelkie stałe niestandardowych dla aplikacji w taki sposób, w tym polu tekstowym. Wpisy powinny być rozdzielone przecinkami, za pomocą tego formularza: **Nazwa1 = "Wartość1," Nazwa2 = "Wartość2", nazwa3 = "Wartość3"**.  
  
## <a name="other-settings"></a>Inne ustawienia  
 **Generuj zestawy serializacji**  
 To ustawienie określa, czy kompilator utworzy zestawy serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania klasy <xref:System.Xml.Serialization.XmlSerializer> Jeśli ta klasa jest używana do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na **automatycznie**, która określa, że zestawy serializacji będą generowane tylko wtedy, gdy używasz <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do XML. **Wyłącz** Określa, że zestawy serializacji nigdy nie są generowane, niezależnie od tego, czy kod używa <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, że zestawy serializacji zawsze będą generowane. Zestawy serializacji noszą `TypeName`. XmlSerializers.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
