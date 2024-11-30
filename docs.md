# Dokumentacja developmentu EKA.NET

## Konwencje i stosowane praktyki

Aby zachować spójność w kodzie w zespole najlepiej jest utrzymywać ustalone standardy.

De facto w projektach stosowana jest konwencja używana przez Micorosft.
Link: https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions

Dla uproszczenia, przedstawione poniżej są nazwy kownencji nazewnictwa, które będą potem stosowane do opisu praktyk:
- PascalCase - nazwa zaczyna się z dużej litery, każde osobne słowo z dużej litery
- camelCase - nazwa zaczyna się z małej litery, każde osobne słowo z dużej litery
- snake_case - nazwy z małych liter, słowa oddzielane podkreślnikiem
- kebab-case - nazwy z małych liter, słowa oddzielane pauzą

Oraz:
- Prefix - przedrostek np. "I" dla interfejsów - IDisposable
- Suffix - przyrostek np. "Exception" dla klas wyjątków - FileNotFoundException

Zaczynając od C#:
- Wszystko co związane z kodem musi być pisane w języku angielskim, również komentarze - wyjątkami są stringi i komunikaty widoczne dla użytkownika


Konwencje nazewnictwa:
- Klasy, Enumy, Structy, Rekordy i metody - PascalCase
- Properties (właściwości) - PascalCase
- Pola prywatne - camelCase (zaczynające się od podkreślenia)
- Interfejsy - PascalCase (zaczynające się z literą "I")
- Constants (stałe) - PascalCase
  
Przykład dla referencji:
```csharp
public class BankAccount : IDepositable
{
    public string Owner { get; set; }

    private decimal _balance;

    public void Deposit(decimal amount)
    {
        _balance -= amount;
    }

    public override string ToString()
    {
        return $"Bank account for {Owner} with balance of {_balance}";
    }
}
```

Dobre praktyki i uwagi:
- Każda metoda asynchroniczna za wyjątkiem endpointów powinna mieć suffix `Async`
- Unikamy committowania linijek z connectionstringami do bazy danych

## Jak pracować?

Używamy Gita. Osobiście do pracy z gitem polecam zapoznać się z dowolnym GUI do tego przeznaczonym, np. GitKraken, SourceTree, czy GitHub Desktop (osobiście polecam Git Fork lub SourceGit).

Sposób pracy z Gitem będzie najważniejszy przy pracy w zespole dlatego warto zapoznać się z najprostszymi a zarazem najważniejszymi komendami:
- `git pull` - pobiera zmiany z repozytorium zdalnego
- `git add .` - dodaje wszystkie zmiany do commita
- `git commit -m "Wiadomość"` - commituje zmiany z wiadomością
- `git push` - wysyła zmiany na repozytorium zdalne
- `git checkout -b nazwa-brancha` - tworzy nowego brancha i przechodzi na niego
- `git checkout nazwa-brancha` - przechodzi na istniejący branch
- `git branch nazwa-brancha` - tworzy nowego brancha

**Ważne!!!**
Aby główne repozytorium było uporządkowane i przejrzyste, zaleca się pracę na swoim forku.
W przypadku chęci dodania zmian do głównego repozytorium należy stworzyć Pull Requesta z własnego forka do głównego repozytorium a następnie czekać na akceptację osób odpowiedzialnych za pomoc przy projekcie (np. lidera koła).

Dobrą praktyką jest tworzenie commitów, których opis jest zwięzły, jednoznaczny a zarazem dokładnie opisuje zmiany jakie zostały wprowadzone. Należy tutaj znaleźć złoty środek, nie przekraczać 50-70 znaków ale też nie pisać np. "fix", "fix bug", "poprawki" itp.

Umówmy się, że nazwy commitów pisane będą po angielsku zaś dyskusja pod pull requestami już po polsku.