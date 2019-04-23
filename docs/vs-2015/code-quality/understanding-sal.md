---
title: Zrozumienie SAL | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: e4c9884517120647e8d0d5bff263496900c2318c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104021"
---
# <a name="understanding-sal"></a>Poznanie SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język adnotacji kod źródłowy firmy Microsoft (SAL) zawiera zbiór adnotacji, które służy do opisywania, jak funkcja korzysta z jego parametrów, założeń, które ułatwia o nich i gwarancji, które to sprawia, że po zakończeniu tej operacji. Adnotacje są zdefiniowane w pliku nagłówkowym `<sal.h>`. Visual Studio analizy kodu dla języka C++ używa adnotacji SAL, aby zmodyfikować jego analiza funkcji. Aby uzyskać więcej informacji na temat SAL w wersji 2.0 dla opracowywania sterowników Windows zobacz [SAL adnotacji dla Windows sterowniki 2.0](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Natywnie C i C++ umożliwiają tylko ograniczone dla deweloperów spójnie express intencji i inwariancja. Za korzystanie z adnotacji SAL, wystarczy opisać funkcji bardziej szczegółowo, aby deweloperzy, którzy są korzystanie z nich można lepiej zrozumieć, jak z nich korzystać.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Co to jest SAL i dlaczego należy jej używać?  
 Krótko mówiąc, SAL jest niedrogą metodę, aby umożliwić kompilatorowi Sprawdź swój kod.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL sprawia, że kod stały się bardziej wartościowe  
 SAL może pomóc Państwu jak najlepiej projektu kodu bardziej zrozumiały dla ludzi i narzędzia do analizy kodu. Rozważmy następujący przykład pokazujący funkcji środowiska uruchomieniowego C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Można stwierdzić, ta funkcja nie? Gdy funkcja jest zaimplementowana lub o nazwie, niektóre właściwości muszą być utrzymywane, aby sprawdzić ich poprawność program. Po prostu patrząc na deklarację, takiego jak w przykładzie, nie wiadomo, jakie są. Bez adnotacji SAL trzeba polegać na dokumentacji lub komentarze w kodzie. Poniżej przedstawiono w dokumentacji MSDN dla `memcpy` jest wyświetlany komunikat:  
  
> "Kopii liczba bajtów src do miejsca docelowego. Jeśli źródłowe i docelowe nakładają się na siebie, zachowanie memcpy jest niezdefiniowane. Memmove — należy używać do obsługi nakładających się regionów.   
> **Uwaga dotycząca zabezpieczeń:** Upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji zobacz unikanie przepełnień bufora."  
  
 Dokumentacja zawiera kilka bitów informacje, które sugerują, kod musi obsługiwać niektórych właściwości, aby sprawdzić ich poprawność program:  
  
- `memcpy` kopiuje `count` bajtów z bufor źródłowy do bufora docelowego.  
  
- Bufor docelowy musi być przynajmniej tak duże jak bufor źródłowy.  
  
  Jednak kompilator nie może odczytać dokumentacji lub nieformalny komentarzy. Nie wie, że istnieje relacja między dwoma buforów i `count`, i go także nie może skutecznie odgadnięcia o relacji. SAL może dostarczyć bardziej przejrzysty o właściwościach i implementacji funkcji sumy, jak pokazano poniżej:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Należy zauważyć, że tymi adnotacjami przypominają informacje przedstawione w dokumentacji MSDN, ale są bardziej zwięzłe i stosują semantycznego wzorca. Podczas odczytywania ten kod może szybko zrozumieć właściwości tej funkcji i jak uniknąć problemów z zabezpieczeniami przepełnienie buforu. Jeszcze lepsze semantycznego wzorców, które zapewnia SAL może poprawić skuteczności i efektywności narzędzi analizy kodu automatyczne wczesne odnajdywania potencjalnych błędów. Wyobraź sobie, że ktoś zapisuje tej implementacji pracowały `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Ta implementacja zawiera typowych błędów wyłączona po drugim. Na szczęście Autor kodu uwzględnione adnotacji SAL rozmiar buforu — narzędzie do analizy kodu można przechwytywać usterki, analizując tę funkcję samodzielnie.  
  
### <a name="sal-basics"></a>Podstawy SAL  
 SAL definiuje cztery podstawowe rodzaje parametrów, które są pogrupowane według wzorca użycia.  
  
|Kategoria|Parametr adnotacji|Opis|  
|--------------|--------------------------|-----------------|  
|**Dane wejściowe, aby wywołał funkcję**|`_In_`|Dane są przekazywane do funkcji o nazwie i jest traktowana jako tylko do odczytu.|  
|**Dane wejściowe, aby wywołał funkcję i dane wyjściowe do obiektu wywołującego**|`_Inout_`|Można używać danych jest przekazywany do funkcji i potencjalnie modyfikować.|  
|**Dane wyjściowe do obiektu wywołującego**|`_Out_`|Obiekt wywołujący tylko miejsce dla wywołanej funkcji do zapisu. Wywołana funkcja zapisuje dane w tej dziedzinie.|  
|**Dane wyjściowe wskaźnika do obiektu wywołującego**|`_Outptr_`|Podobnie jak **dane wyjściowe do obiektu wywołującego**. Wartość, która jest zwracana przez funkcję o nazwie jest wskaźnikiem.|  
  
 Te cztery podstawowego adnotacje bardziej jako jawne można ustawić na różne sposoby. Domyślnie parametry wskaźnika adnotacjami są zakłada się, że wymagane — muszą one mieć wartości NULL dla funkcji, które zakończyło się sukcesem. Najczęściej używane odmianą podstawowe adnotacje wskazuje, że parametr wskaźnika jest opcjonalne, jeśli ma wartość NULL, funkcja może nadal się powieść, w tym swoją pracę.  
  
 W tej tabeli przedstawiono sposób odróżnić wymaganych i opcjonalnych parametrów:  
  
||Parametry są wymagane|Parametry są opcjonalne|  
|-|-----------------------------|-----------------------------|  
|**Dane wejściowe, aby wywołał funkcję**|`_In_`|`_In_opt_`|  
|**Dane wejściowe, aby wywołał funkcję i dane wyjściowe do obiektu wywołującego**|`_Inout_`|`_Inout_opt_`|  
|**Dane wyjściowe do obiektu wywołującego**|`_Out_`|`_Out_opt_`|  
|**Dane wyjściowe wskaźnika do obiektu wywołującego**|`_Outptr_`|`_Outptr_opt_`|  
  
 Adnotacje identyfikowania możliwych wartości niezainicjowany i używa nieprawidłowego wskaźnika o wartości null, w sposób formalny i dokładne. Przekazanie wartości NULL do wymaganego parametru może spowodować awarię lub może spowodować, że kod błędu "nie powiodło się", ma zostać zwrócona. W obu przypadkach funkcja nie może powieść się w tym swojego zadania.  
  
## <a name="sal-examples"></a>Przykłady SAL  
 W tej sekcji przedstawiono przykłady kodu dla podstawowych adnotacji SAL.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Aby znaleźć usterek przy użyciu narzędzie do analizy kodu programu Visual Studio  
 W przykładach narzędzia analizy kodu w usłudze Visual Studio jest używany razem z adnotacji SAL do znalezienia usterek kodu. Oto jak to zrobić.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Aby użyć narzędzia analizy programu Visual Studio code i SAL  
  
1. W programie Visual Studio Otwórz projekt C++, który zawiera adnotacji SAL.  
  
2. Na pasku menu wybierz **kompilacji**, **Uruchom analizę kodu dla rozwiązania**.  
  
    Należy wziąć pod uwagę \_w\_ przykładzie w tej sekcji. To ostrzeżenie jest wyświetlane, po uruchomieniu analizy kodu na nim:  
  
   > **C6387 Nieprawidłowa wartość parametru**   
   > "Pinta" może być "0": jest to niespójne ze specyfikacją funkcji "InCallee".  
  
### <a name="example-the-in-annotation"></a>Przykład: \_w\_ adnotacji  
 `_In_` Adnotacja wskazuje, że:  
  
- Parametr musi być prawidłowy i nie zostaną zmodyfikowane.  
  
- Funkcja odczyta tylko z jednym elementem buforu.  
  
- Obiekt wywołujący, musisz podać buforu i zainicjować go.  
  
- `_In_` Określa "read-only". Powszechnym błędem jest do zastosowania `_In_` do parametru, którą powinien posiadać `_Inout_` adnotacji zamiast tego.  
  
- `_In_` jest dozwolone, ale jest ignorowana przez analizator na nie będącego wskaźnikiem wartości skalarnych.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Jeśli używasz programu Visual Studio Code Analysis w tym przykładzie, sprawdza czy funkcja wywołująca przekazać wskaźnik zerowy do zainicjowane bufor w poszukiwaniu `pInt`. W tym przypadku `pInt` wskaźnik nie może mieć wartości NULL.  
  
### <a name="example-the-inopt-annotation"></a>Przykład: \_In_opt\_ adnotacji  
 `_In_opt_` jest taka sama jak `_In_`, z tą różnicą, że parametr wejściowy może mieć wartości NULL, i w związku z tym, funkcja powinna sprawdzać, czy to.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, czy funkcja przed sprawdza ją pod kątem wartości NULL uzyskuje dostęp do buforu.  
  
### <a name="example-the-out-annotation"></a>Przykład: \_Się\_ adnotacji  
 `_Out_` obsługuje typowy scenariusz, w którym wskaźnika inną niż NULL, który wskazuje element buforu jest przekazywany w, a funkcja inicjuje element. Obiekt wywołujący nie ma zainicjować buforu przed wywołaniem; wywołana funkcja zobowiązuje się do zainicjowania go przed jego zwracaniem.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Narzędzie do analizy kodu programu Visual Studio sprawdza, czy obiekt wywołujący przekazuje wskaźnik ZEROWY do buforu dla `pInt` i że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
### <a name="example-the-outopt-annotation"></a>Przykład: \_Out_opt\_ adnotacji  
 `_Out_opt_` jest taka sama jak `_Out_`, z tą różnicą, że parametr może mieć wartości NULL, i w związku z tym, funkcja powinna sprawdzać, czy to.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, czy ta funkcja sprawdza wartość NULL, przed `pInt` jest wyłuskiwany i jeśli `pInt` nie ma wartości NULL, że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
### <a name="example-the-inout-annotation"></a>Przykład: \_Inout\_ adnotacji  
 `_Inout_` Umożliwia dodawanie adnotacji do parametru wskaźnika, który może zostać zmieniona przez funkcję. Wskaźnik musi wskazywać prawidłowe dane zainicjowany przed wywołaniem, a nawet w przypadku jego zmiany, nadal musi mieć prawidłową wartość przy powrocie. Adnotacja Określa, czy funkcja mogą swobodnie odczytu i zapisu w buforze jeden element. Obiekt wywołujący, musisz podać buforu i zainicjować go.  
  
> [!NOTE]
>  Podobnie jak `_Out_`, `_Inout_` należy zastosować do modyfikowalnych wartości.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, że obiekty wywołujące przekazać wskaźnik ZEROWY do zainicjowane bufor w poszukiwaniu `pInt`oraz że przed return `pInt` jest nadal różna od NULL i rozmiar buforu jest zainicjowany.  
  
### <a name="example-the-inoutopt-annotation"></a>Przykład: \_Inout_opt\_ adnotacji  
 `_Inout_opt_` jest taka sama jak `_Inout_`, z tą różnicą, że parametr wejściowy może mieć wartości NULL, i w związku z tym, funkcja powinna sprawdzać, czy to.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, czy ta funkcja sprawdza NULL przed uzyskuje dostęp do buforu, a jeśli `pInt` nie ma wartości NULL, że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
### <a name="example-the-outptr-annotation"></a>Przykład: \_Outptr\_ adnotacji  
 `_Outptr_` Umożliwia dodawanie adnotacji, parametr, który jest przeznaczony do zwracają wskaźnik.  Parametr, sama nie powinien być wartość NULL i wywołana funkcja zwraca wskaźnik ZEROWY i danych zainicjowanych wskazuje ten wskaźnik.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, czy obiekt wywołujący przekazuje wskaźnik ZEROWY `*pInt`, oraz że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
### <a name="example-the-outptropt-annotation"></a>Przykład: \_Outptr_opt\_ adnotacji  
 `_Outptr_opt_` jest taka sama jak `_Outptr_`, z tą różnicą, że parametr jest opcjonalny — obiekt wywołujący można przekazać wskaźnik o wartości NULL dla parametru.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio Code Analysis weryfikuje, czy ta funkcja sprawdza wartość NULL, przed `*pInt` jest wyłuskiwany, oraz że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Przykład: \_Powodzenie\_ adnotacji w połączeniu z \_Out\_  
 Adnotacje można zastosować do większości obiektów.  W szczególności można dodawać adnotacje do całej funkcji.  Jest jedną z najbardziej typowe właściwości funkcji, można go powodzenie lub niepowodzenie. Zachowując takich jak skojarzenie między bufor oraz jego rozmiaru, C/C++ nie funkcja powodzenia lub niepowodzenia. Za pomocą `_Success_` adnotacji, można powiedzieć, jakie sukces dla funkcji wygląda następująco.  Parametr `_Success_` adnotacji jest po prostu wyrażeniem, że znajduje się wartość true wskazuje, że funkcja zakończyła się pomyślnie. Wyrażenie może być wszystko, co może obsługiwać analizatora adnotacji. Efekty adnotacje po powrocie funkcji są stosowane tylko w przypadku, gdy funkcja się powiedzie. Ten przykład pokazuje, jak `_Success_` wchodzi w interakcję z `_Out_` do postępują właściwie. Można użyć słowa kluczowego `return` do reprezentowania wartości zwracanej.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_` Adnotacji powoduje, że program Visual Studio analizy kodu do sprawdzania poprawności, obiekt wywołujący przekazuje wskaźnik ZEROWY do buforu dla `pInt`, oraz że bufor jest inicjowany przez funkcję, przed jego zwracaniem.  
  
## <a name="sal-best-practice"></a>Najlepszym rozwiązaniem jest SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Dodawanie adnotacji do istniejącego kodu  
 SAL jest zaawansowaną technologię, która pomoże Ci zwiększenia bezpieczeństwa i niezawodności swój kod. Po możesz dowiedzieć się, jak SAL, można zastosować nowych umiejętności, do codziennej pracy. W nowym kodzie można użyć specyfikacji na podstawie SAL zgodnie z projektem w całym; w przypadku starszego kodu możesz stopniowo dodawać adnotacje i zwiększając korzyści w każdym razem, gdy.  
  
 Nagłówki publicznych firmy Microsoft są już adnotacji. W związku z tym zaleca się, że w swoich projektach najpierw dodawania adnotacji typu liść węzła i funkcje, które wywołują interfejsów API systemu Win32, aby uzyskać największe korzyści.  
  
### <a name="when-do-i-annotate"></a>Gdy adnotacji  
 Poniżej przedstawiono kilka wskazówek:  
  
- Dodawanie adnotacji do wszystkich parametrów wskaźnika.  
  
- Dodawanie adnotacji do adnotacji zakres wartości, tak, aby analiza kodu może zapewnić bezpieczeństwo buforu i wskaźnik.  
  
- Dodawanie adnotacji do reguły blokowania i blokowanie efekty uboczne. Aby uzyskać więcej informacji, zobacz [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md).  
  
- Dodawanie adnotacji do właściwości sterownika i inne właściwości specyficzne dla domeny.  
  
  Lub możesz dodawać adnotacje do wszystkich parametrów, aby zapewnić usługi elementu intent wyczyść w całym i ułatwiają sprawdzanie, czy zostały wykonane adnotacji.  
  
## <a name="related-resources"></a>Powiązane zasoby  
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia liczby błędów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
