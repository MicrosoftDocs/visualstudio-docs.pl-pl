---
title: Okno dialogowe Zaawansowane ustawienia kompilatora (Visual Basic) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba666b0ff5544b185f82a66c78d6259e9f1268fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651766"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Zaawansowane ustawienia kompilatora (Visual Basic) — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą okna dialogowego **Ustawienia AdvancedCompiler** **projektanta projektu** można określić zaawansowane właściwości kompilacji — konfiguracja. To okno dialogowe dotyczy tylko projektów Visual Basic.

### <a name="to-access-this-dialog-box"></a>Aby uzyskać dostęp do tego okna dialogowego

1. W **Eksplorator rozwiązań**wybierz węzeł projektu (nie węzeł **rozwiązania** ).

2. W menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **kompilacja** .

3. Na [stronie kompilacja, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)wybierz **konfigurację** i **platformę**. W uproszczonych konfiguracjach kompilacji listy **konfiguracji** i **platformy** nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [debugowanie i wydanie konfiguracji projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

4. Kliknij pozycję **Zaawansowane opcje kompilacji**.

   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="optimizations"></a>Optymalizacje
 Poniższe opcje określają optymalizacje, które w niektórych przypadkach sprawiają, że plik programu jest mniejszy, szybsze działanie programu lub przyspieszenie procesu kompilacji.

 **Usuń sprawdzanie przepełnienia liczby całkowitej** To pole wyboru jest domyślnie wyczyszczone, aby włączyć sprawdzanie przepełnienia liczby całkowitej. Zaznacz to pole wyboru, aby usunąć sprawdzanie przepełnienia liczby całkowitej. Jeśli zaznaczysz to pole wyboru, obliczenia liczby całkowitej mogą być szybsze. Jeśli jednak usuniesz sprawdzanie przeciążenia i przepełnienie pojemności typu danych, nieprawidłowe wyniki mogą być przechowywane bez zgłaszania błędu.

 Jeśli sprawdzane są warunki przepełnienia, a operacja całkowita przekracza przepływ, zostanie zgłoszony wyjątek <xref:System.OverflowException>. Jeśli warunki przepełnienia nie są zaznaczone, operacje typu Integer nie generują wyjątku.

 **Włącz optymalizacje** To pole wyboru jest domyślnie wyczyszczone, aby wyłączyć optymalizacje kompilatora. Zaznacz to pole wyboru, aby włączyć optymalizacje kompilatora. Optymalizacje kompilatora sprawiają, że plik wyjściowy jest mniejszy, szybszy i bardziej wydajny. Jednakże, ponieważ optymalizacje powodują ponowne rozmieszczanie kodu w pliku wyjściowym, optymalizacje kompilatora mogą utrudniać debugowanie.

 **Adres podstawowy biblioteki DLL** To pole tekstowe wyświetla domyślny adres bazy DLL w formacie szesnastkowym. W obszarze Biblioteka klas i projekty bibliotek formantów można użyć tego pola tekstowego, aby określić adres podstawowy, który ma być używany podczas tworzenia biblioteki DLL.

 **Generuj informacje o debugowaniu** Z listy wybierz opcję **Brak**, **pełna**lub **PDB** . **Brak** określa, że nie są generowane żadne informacje debugowania. **Pełna** określa, że mają zostać wygenerowane pełne informacje o debugowaniu, a **PDB-tylko** określa, że generowane są tylko informacje debugowania PDB. Domyślnie ta opcja jest ustawiona na **pełna**.

## <a name="compilation-constants"></a>Stałe kompilacji
 Stałe kompilacji warunkowej mają efekt podobny do tego w przypadku używania dyrektywy preprocesora [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) w pliku źródłowym, z wyjątkiem tego, że stałe są zdefiniowane i mają zastosowanie do wszystkich plików w projekcie. Możesz użyć stałych kompilacji warunkowej razem z [#If... Następnie... #Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) dyrektywa do kompilowania plików źródłowych warunkowo. Zobacz [Kompilacja warunkowa](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).

 **Zdefiniuj stałą DEBUG** To pole wyboru jest domyślnie zaznaczone, co oznacza, że jest ustawiona stała debugowania.

 **Zdefiniuj stałą Trace** To pole wyboru jest domyślnie zaznaczone, co oznacza, że jest ustawiona stała śledzenia.

 **Stałe niestandardowe** Wprowadź dowolne niestandardowe stałe dla aplikacji w tym polu tekstowym. Wpisy powinny być rozdzielane przecinkami, przy użyciu tej formy: **Name1 = "wartość1", NAME2 = "wartość2", nazwa3 = "wartość3"** .

## <a name="other-settings"></a>Inne ustawienia
 **Generuj zestawy serializacji** To ustawienie określa, czy kompilator ma tworzyć zestawy serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania <xref:System.Xml.Serialization.XmlSerializer>, jeśli użyto tej klasy do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na wartość **automatycznie**, co oznacza, że zestawy serializacji są generowane tylko wtedy, gdy użyto <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do formatu XML. **Wyłączone** określa, że zestawy serializacji nigdy nie są generowane, bez względu na to, czy kod używa <xref:System.Xml.Serialization.XmlSerializer>. **Na** określa, że zestawy serializacji zawsze są generowane. Zestawy serializacji mają nazwę `TypeName`. XmlSerializers. dll.

## <a name="see-also"></a>Zobacz też
 [Strona kompilowania, Projektant projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
