# Semana3Laboratorio
use neptuno
drop procedure usp_Total

create procedure USP_FECHAFECHA
@FEC1 datetime,
@FEC2 datetime
as
select * from Pedidos where FechaPedido between @FEC1 and @FEC2

create procedure usp_detalle
@IdPedido int
as
select * from detallesdepedidos where idpedido = @IdPedido

create procedure usp_Total
@IdPedido int,
@Total money output
as
begin
select @Total = SUM(preciounidad*cantidad) - descuento from detallesdepedidos
where idpedido = @IdPedido
group by idpedido,descuento
end





create procedure usp_Total
@IdPedido INT,
@Total MONEY OUTPUT
AS 
BEGIN
SET @Total =(SELECT SUM(PrecioUnidad*cantidad)
from detallesdepedidos
where idpedido=@IdPedido)
End
