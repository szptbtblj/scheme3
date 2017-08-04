# scheme3
(define diff
  (lambda (fx)
    (cond ((number? fx) 0)
          ((equal? fx 'x) 1)
          ((equal? (car fx) '+)  (cons '+ (map (lambda (x) (diff x)) (cdr fx))))
          ((equal? (car fx) '-)  (cons '- (map (lambda (x) (diff x)) (cdr fx))))
          ((equal? (car fx) '*)  (list '+ (append '(*) (cons (car (cdr fx)) (map (lambda (x) (diff x)) (cdr (cdr fx))))) (append '(*) (cons (diff (car (cdr fx))) (cdr (cdr fx))))))
          ((equal? (car fx) '**) (cdr (cdr fx)))
          (else 2)
          )
    ))
