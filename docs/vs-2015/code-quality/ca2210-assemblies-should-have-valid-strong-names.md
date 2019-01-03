---
title: 'CA2210: Zestawy powinny mieć prawidłowe silne nazwy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 571c85933fda472600dbbc08749a3c29ccfa0701
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990248"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Zestawy powinny mieć prawidłowe silne nazwy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw jest podpisany silną nazwą, nie można zweryfikować silnej nazwy lub silnej nazwy nie jest prawidłowym bez bieżące ustawienia rejestru komputera.

## <a name="rule-description"></a>Opis reguły
 Ta zasada pobiera i weryfikuje silną nazwę zestawu. Naruszenie wystąpi w przypadku spełnienia dowolnego z następujących czynności:

- Zestaw ma silną nazwę.

- Zestaw został zmieniony po zarejestrowaniu się.

- Zestaw jest podpisany z opóźnieniem.

- Zestaw został niepoprawnie podpisany lub podpisywanie nie powiodło się.

- Zestaw wymaga ustawienia rejestru w celu przekazania weryfikacji. Na przykład narzędzie silnych nazw (Sn.exe) został użyty do pominięcia weryfikacji dla zestawu.

  Silna nazwa chroni klientów przed nieświadomym ładowaniem zestawu, który został zmieniony. Zestawy bez silnej nazwy nie powinny być wdrażane poza bardzo ograniczonymi scenariuszami. Jeśli użytkownik udostępnia lub dystrybuuje zestawy, które nie są poprawnie podpisane, zestaw może zostać zmieniony, środowisko uruchomieniowe języka wspólnego może nie załadować zestawu lub użytkownik będzie musiał wyłączyć weryfikację na swoim komputerze. Ma to zestaw bez silnej nazwy z następujące wady:

- Nie można zweryfikować jej źródła.

- Środowisko uruchomieniowe języka wspólnego nie ostrzec użytkowników, jeśli zawartość zestawu została zmieniona.

- Nie można załadować do pamięci podręcznej zestawów globalnych.

  Należy pamiętać, że można załadować i przeanalizować zestawu podpisanego z opóźnieniem, należy wyłączyć weryfikację zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Aby utworzyć plik klucza**

 Użyj jednej z następujących procedur:

- Za pomocą narzędzia Assembly Linker (Al.exe) dostarczonych przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestawu SDK.

- Aby uzyskać [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 1.0 lub 1.1, użyj jednej <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> lub <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atrybutu.

- Aby uzyskać [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], użyj jednej `/keyfile` lub `/keycontainer` — opcja kompilatora [/KeyFile (Określ klucz lub parę klucz Aby podpisać zestaw)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) lub  [ /KeyContainer (Określ kontener klucza, aby podpisać zestaw)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) — opcja konsolidatora w języku C++).

  **Aby podpisać zestaw silną nazwą w programie Visual Studio**

1. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz swoje rozwiązanie.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości.**

3. Kliknij przycisk **podpisywanie** , a następnie wybierz pozycję **Podpisz zestaw** pole wyboru.

4. Z **wybierz plik klucza o silnej nazwie**, wybierz opcję **New**.

    **Utwórz klucz silnej nazwy** oknie zostanie wyświetlona.

5. W **nazwę pliku klucza**, wpisz nazwę dla swojego klucza silnej nazwy.

6. Wybierz, czy klucz jest chroniony hasłem, a następnie kliknij przycisk **OK**.

7. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **kompilacji**.

   **Aby podpisać zestaw silną nazwą poza programem Visual Studio**

-   Użyj narzędzie silnych nazw (Sn.exe), które są dostarczane przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zestawu SDK. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Tylko Pomijaj ostrzeżeń dla tej reguły, jeśli zestaw jest używany w środowisku, w których naruszeniu zawartość nie jest wymagana.

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName><xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Instrukcje: Podpisywanie zestawu silną nazwą](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (narzędzie silnych nazw)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
