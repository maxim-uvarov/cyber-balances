## Arbitrage in Bostrom, Space-Pussy, Osmosis and Crescent Networks

### Pools

#### [Bostrom Pools](https://cyb.ai/warp)  
#### [Space-Pussy Pools](https://cyb.ai/warp)  
#### [Osmosis Pools](https://frontier.osmosis.zone/pools)
- [BOOT-ATOM](https://info.osmosis.zone/pool/596)  
- [BOOT-OSMO](https://info.osmosis.zone/pool/597)  
- [BOOT-WETH (Gravity)](https://info.osmosis.zone/pool/911)  
- [BOOT-WETH (Axelar)](https://info.osmosis.zone/pool/912)  
- [BOOT-DOT](https://info.osmosis.zone/pool/919)  
#### [Crescent Pools](https://app.crescent.network/farm)

### Price Formulas
#### Bostrom and Space-Pussy

[Tendermint Liquidity Module Light Paper](https://github.com/tendermint/liquidity/blob/develop/doc/LiquidityModuleLightPaper_EN.pdf)

Formulas without orderbook matching (Liquidity Pool Model only)   

<img src="https://latex.codecogs.com/png.image?\inline\dpi{150}\bg{white}Price&space;=&space;\frac{Target\&space;Coin\&space;Pool\&space;Amount\&space;*\&space;(1&space;-&space;Pool\&space;Fee)}{Source\&space;Coin\&space;Pool\&space;Amount\&space;&plus;\&space;2\&space;*\&space;Source\&space;Coin\&space;Amount}" />
<img src="https://latex.codecogs.com/png.image?\inline\dpi{175}\bg{white}Target\&space;Coin\&space;Amount&space;=&space;\frac{Source\&space;Coin\&space;Amount\&space;*\&space;Target\&space;Coin\&space;Pool\&space;Amount\&space;*\&space;(1&space;-&space;Pool\&space;Fee)}{Source\&space;Coin\&space;Pool\&space;Amount\&space;&plus;\&space;2\&space;*\&space;Source\&space;Coin\&space;Amount}" />

where _Pool Fee = 0.003_ as most common value

#### Osmosis
[Module Gamm documentation](https://docs.osmosis.zone/osmosis-core/modules/gamm)

<img src="https://latex.codecogs.com/png.image?\inline\dpi{200}\bg{white}Price&space;=&space;\frac{Target\&space;Coin\&space;Pool\&space;Amount\&space;*\&space;(1&space;-&space;Pool\&space;Fee)}{Source\&space;Coin\&space;Pool\&space;Amount\&space;&plus;\&space;(1&space;-&space;Pool\&space;Fee)\&space;*\&space;Source\&space;Coin\&space;Amount}\&space;*\&space;\frac{Source\&space;Coin\&space;Pool\&space;Weight}{Target\&space;Coin\&space;Pool\&space;Weight}" />
<img src="https://latex.codecogs.com/png.image?\inline\dpi{175}\bg{white}Target\&space;Coin\&space;Amount&space;=&space;\frac{Source\&space;Coin\&space;Amount\&space;*\&space;Target\&space;Coin\&space;Pool\&space;Amount\&space;*\&space;(1&space;-&space;Pool\&space;Fee)}{Source\&space;Coin\&space;Pool\&space;Amount\&space;&plus;\&space;(1&space;-&space;Pool\&space;Fee)\&space;*\&space;Source\&space;Coin\&space;Amount}\&space;*\&space;\frac{Source\&space;Coin\&space;Pool\&space;Weight}{Target\&space;Coin\&space;Pool\&space;Weight}" />

### Analytics

#### [Bostrom Revenue and Price Model](revenue_model.ipynb)

#### [Bostrom and Space-Pussy Related Pools Liquidity](pools_liquidity_in_gh.ipynb)

#### [Search the Best Arbitrage in Bostrom, Osmosis and Space-Pussy Pools](search_arbitrage.ipynb)

#### [Bostrom and Space-Pussy Swap Optimization. Finding the Best Way to Swap Coins](swap_optimization.ipynb)

#### [Bostrom and Space-Pussy Deposit Calculation for a direct transaction](deposit_calculation.ipynb)  
it's usually more convenient to use the [cyb.ai](https://cyb.ai/warp/add-liquidity)

### Get Data
#### Pools Data
```python
from src.data_extractors import get_pools, get_prices, get_price_enriched

pools_df = get_pools(networks=['bostrom', 'space-pussy', 'osmosis', 'crescent'], bostrom_related_osmo_pools=None)
```
#### Direct Prices
```python
price_df = get_prices(pools_df=pools_df)
```
#### Enriched Prices
```python
price_df = get_price_enriched(price_df=price_df, base_coin_denom='uosmo')
```