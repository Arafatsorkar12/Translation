# Translation
###First__MAke_Middleware 
```php
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;

class LanguageControlMiddleware
{

    public function handle(Request $request, Closure $next)
    {
        if (session()->has('locale')) {
            app()->setLocale(session('locale'));
        }
        return $next($request);
    }
}
```

### Now Make Route 

```php
Route::get('lang/{locale}', function ($locale) {
    session(['locale' => $locale]);
    return redirect()->back();
})->name('lang.switch');

```
### Make button That change Lang
```php
<li class="light-10" title="Change Language">
                    @if(app()->getLocale() === 'en')
                        <a href="{{ route('lang.switch', 'bn') }}"  style="background-color: #00BE67 !important; color: #ffffff !important; font-size: 15px; font-weight: bolder !important;">বাংলা</a>
                    @else
                        <a href="{{ route('lang.switch', 'en') }}" style="background-color: #00BE67 !important; color: #ffffff !important; font-size: 15px; font-weight: bolder !important;">English</a>
                    @endif
                </li>
```

### Now reate Lang File 

```php
 
├── resources
│   └──  lang
          ├── bn ->language.php
          └── en ->language.php
```
### Now Make blade File , Any Lang Make same Name File 
like ::: bn ->language.php


