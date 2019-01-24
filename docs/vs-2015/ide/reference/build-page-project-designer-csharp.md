---
title: Strona kompilacji, Projektant projektu (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 066535309c7001c3f7a951f68321f7530a06ed05
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805324"
---
# <a name="build-page-project-designer-c"></a>Strona kompilacji, Projektant projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Użyj **kompilacji** strony **projektanta projektu** do określania właściwości konfiguracji kompilacji projektu. Ten temat dotyczy [!INCLUDE[csprcs](../../includes/csprcs-md.md)] wyłącznie dla projektów.  
  
 Aby uzyskać dostęp do **kompilacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **kompilacji** kartę.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Konfiguracja i platforma  
 Poniższe opcje pozwalają wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.  
  
> [!NOTE]
>  Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. Dlatego te opcje nie są wyświetlane. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Konfiguracja**  
 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Te ustawienia mogą mieć **aktywna (debugowanie)** (to jest wartość domyślna), **debugowania**, **wersji**, lub **wszystkie konfiguracje**.  
  
 **Platforma**  
 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawieniem domyślnym jest **aktywna (dowolny procesor CPU)**. Możesz zmienić aktywną platformę przy użyciu **programu Configuration Manager**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="general"></a>Ogólne  
 Poniższe opcje umożliwiają skonfigurowanie kilku ustawień kompilatora języka C#.  
  
 **Symbole kompilacji warunkowej**  
 Określa symbole, na którym ma zostać wykonana zostanie kompilacja warunkowa. Oddziel symbole średnikiem (";"). Aby uzyskać więcej informacji, zobacz [/ define (opcje kompilatora C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **Zdefiniuj stałą DEBUG**  
 Definiuje DEBUG jako symbol we wszystkich plikach kodu źródłowego w Twojej aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:DEBUG` opcji wiersza polecenia.  
  
 **Zdefiniuj stałą TRACE**  
 Definiuje TRACE jako symbol we wszystkich plikach kodu źródłowego w Twojej aplikacji. Wybranie tej opcji jest równoważne użyciu `/define:TRACE` opcji wiersza polecenia.  
  
 **Docelowy adres CPU**  
 Określa procesor, która ma zostać użyty przez plik wyjściowy. Wybierz **x86** dla dowolnej 32-bitowym procesorze zgodnego z Intel, wybierz **x64** dla dowolnego 64-bitowy procesor zgodnego z Intel, wybierz **ARM** dla procesorów ARM lub wybierz  **Dowolny procesor CPU** do określenia, czy akceptowalny jest każdy procesor. **Dowolny procesor CPU** jest wartością domyślną dla projektów, ponieważ umożliwia aplikacji, aby działała na najszerszym zakresie sprzętu.  
  
 Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **Preferuj 32-bitowe**  
 Jeśli **Preferuj 32 bitowe** pole wyboru jest zaznaczone, aplikacja działa jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. Jeśli pole wyboru jest wyczyszczone, aplikacja działa jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows.  
  
 W przypadku uruchomienia aplikacji jako aplikacji 64-bitowej podwaja się rozmiar wskaźnika, i z innych bibliotek, które są wyłącznie 32-bitowe, mogą wystąpić problemy ze zgodnością. Jest to przydatne do uruchamiania aplikacji 64-bitowych, tylko wtedy, gdy potrzebuje więcej niż 4 GB pamięci lub 64-bitowe instrukcje stanowią istotnie poprawiającą wydajność.  
  
 To pole wyboru jest dostępne tylko wtedy, gdy spełnione są wszystkie następujące warunki:  
  
- Na **Stroka kompilacji**, **platformę docelową** listy jest ustawiona na **dowolny Procesor**.  
  
- Na **strony aplikacji**, **typ danych wyjściowych** lista określa, że projekt jest aplikacją.  
  
- Na **strony aplikacji**, **platformę docelową** lista określa .NET Framework 4.5.  
  
  **Zezwalaj na niebezpieczny kod**  
  Zezwala na kod, który używa [niebezpieczne](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) — słowo kluczowe, aby skompilować. Aby uzyskać więcej informacji, zobacz [/ unsafe (opcje kompilatora C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Optymalizuj kod**  
  Włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne. Aby uzyskać więcej informacji, zobacz [/ optimize (opcje kompilatora C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Błędy i ostrzeżenia  
 Poniższe ustawienia są używane do skonfigurowania opcji błędów i ostrzeżeń dla procesu kompilacji.  
  
 **Poziom ostrzeżeń**  
 Określa poziom wyświetlania ostrzeżeń kompilatora. Aby uzyskać więcej informacji, zobacz [/ warn (opcje kompilatora C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Pomijanie ostrzeżeń**  
 Blokuje zdolność kompilatora do generowania co najmniej jedno ostrzeżenie. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy  
 Poniższe ustawienia są używane do określania, które ostrzeżenia są traktowane jako błędy. Wybierz jedną z poniższych opcji, aby wskazać, pod jakimi warunkami ma zostać zwrócony błąd, jeśli kompilacja napotka ostrzeżenie. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **Brak**  
 Nie traktuje ostrzeżeń jako błędy.  
  
 **Określone ostrzeżenia**  
 Traktuje określone ostrzeżenia jako błędy. Oddziel wiele numerów ostrzeżeń przecinkami lub średnikami.  
  
 **Wszystkie**  
 Traktuje wszystkie ostrzeżenia jako błędy.  
  
## <a name="output"></a>Dane wyjściowe  
 Następujące ustawienia są używane do skonfigurowania opcji wyjściowych dla procesu kompilacji.  
  
 **Ścieżka wyjściowa**  
 Określa położenie plików wyjściowych dla tej konfiguracji projektu. Wprowadź ścieżkę produktu kompilacji w tym polu lub wybierz **Przeglądaj** przycisk, aby określić ścieżkę. Należy zauważyć, że ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, jego zostanie zapisana jako względna. Domyślna ścieżka to bin\Debug lub bin\Release\\. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 Za pomocą uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. **Kompilacji** polecenia **debugowania** menu (F5) umieszcza kompilację w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **kompilacji** polecenia **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release projektu](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plik dokumentacji XML**  
 Określa nazwę pliku do dokumentacji, które będą przetwarzane komentarze. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **Zarejestruj dla współdziałania z modelem COM**  
 Wskazuje, że Twoją zarządzaną aplikacją udostępni obiektu COM (wywołalne opakowanie COM), który umożliwia obiektu COM na interakcję z Twoją zarządzaną aplikacją. **Typ danych wyjściowych** właściwość [strony aplikacji](../../ide/reference/application-page-project-designer-visual-basic.md) z **projektanta projektu** dla tej aplikacji musi być równa **biblioteki klas** w kolejność dla **Zarejestruj dla współdziałania COM** aby była dostępna właściwość. Aby uzyskać przykładową klasę, którą można umieścić w swojej [!INCLUDE[csprcs](../../includes/csprcs-md.md)] aplikacji i udostępniać jako obiekt COM, zobacz [klasa COM — przykład](http://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).  
  
 **Generuj zestaw serializacji**  
 Określa, czy kompilator będzie używał narzędzie generatora serializatora XML (Sgen.exe) do tworzenia zestawów serializacji XML. Zestawy serializacji mogą zwiększyć wydajność uruchamiania klasy <xref:System.Xml.Serialization.XmlSerializer> Jeśli ta klasa jest używana do serializacji typów w kodzie. Domyślnie ta opcja jest ustawiona na **automatycznie**, która określa, że zestawy serializacji będą generowane tylko wtedy, gdy używasz <xref:System.Xml.Serialization.XmlSerializer> do kodowania typów w kodzie do XML. **Wyłącz** Określa, że zestawy serializacji nigdy nie są generowane, niezależnie od tego, czy kod używa <xref:System.Xml.Serialization.XmlSerializer>. **Na** Określa, że zestawy serializacji zawsze będą generowane. Zestawy serializacji noszą `TypeName`. XmlSerializers.dll. Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatora XML (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Zaawansowane**  
 Kliknij, aby wyświetlić [zaawansowane kompilacji okno dialogowe Ustawienia (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)   
 [Opcje kompilatora C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
